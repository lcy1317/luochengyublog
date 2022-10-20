---
title: Ns3 入门踩坑
date: 2022-10-18 22:11:24
tags: Study
categories: Study
author: Lcy
---

# Ns3 一些基础的东西

## 1. 为运行的ns3程序指定参数

在ns3中如果使用了command line去获取读入的参数，例如对于程序段：

```C++
  CommandLine cmd (__FILE__);
  cmd.AddValue ("numNodePairs", "Number of eNodeBs + UE pairs", numNodePairs);
  cmd.AddValue ("simTime", "Total duration of the simulation", simTime);
  cmd.AddValue ("distance", "Distance between eNBs [m]", distance);
  cmd.AddValue ("interPacketInterval", "Inter packet interval", interPacketInterval);
  cmd.AddValue ("useCa", "Whether to use carrier aggregation.", useCa);
  cmd.AddValue ("disableDl", "Disable downlink data flows", disableDl);
  cmd.AddValue ("disableUl", "Disable uplink data flows", disableUl);
  cmd.AddValue ("disablePl", "Disable data flows between peer UEs", disablePl);
  cmd.Parse (argc, argv);

  printf("numNodePairs=%d\n",numNodePairs);  
  printf("distance=%lf\n",distance);
```

如果我们希望指定numNodePairs参数或者distance参数，可以使用如下运行方式：

```shell
./ns3 run '<ns3-program> --arg1=value1 --arg2=value2 ...'
```

参考如上的tutorial给出的运行方式，可以输入如下指令：

```shell
./ns3 run "scratch/lena-simple-epc.cc --numNodePairs=10 --distance=20" --vis
```



## 2.Ns3可视化安装问题

### Assert in TypeId::LookupByName

报错示例：这个是可视化的安装问题。

```shell
assert failed. cond="uid != 0", msg="Assert in TypeId::LookupByName: ns3::VisualSimulatorImpl not found", file=/home/lcy/Desktop/ns3/ns-allinone-3.36.1/ns-3.36.1/src/core/model/type-id.cc, line=833
terminate called without an active exception
```

[(14条消息) NS3报错assert failed. cond="uid != 0", msg="Assert in TypeId::LookupByName: xxx not found", file=../sr_蓝色瞬间的博客-CSDN博客](https://blog.csdn.net/easonchenys/article/details/42419445)

然而这句话并没有什么用处，但是可以知道的是去掉运行命令的--vis可视化可以不报错。

[ns3—可视化工具_三眼二郎的博客-CSDN博客_ns3可视化](https://blog.csdn.net/a6333230/article/details/108296948)

可视化的前期安装。

[PyViz - Nsnam](https://www.nsnam.org/mediawiki/index.php/PyViz#current_ns-3)

[PyViz Installation (google.com)](https://groups.google.com/g/ns-3-users/c/2jTS4vDnsks/m/MnCuHwmcBQAJ)

反正，这几个都试一下吧。



然后，要怎么才能跑起来程序呢？那就是root用户+ns3.35，反正不能非root会跑不起vis，也不能root3.36，他不给你运行。嗯就是如此扯淡。

![image-20221018221019689](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221018221019689.png)

他喵总算可以可视化了。

## 3. 建立一些小东西

### I. 建立一个P2P连接

使用`PointToPointHelper` 可以建立两个`Ptr<Node>`之间的P2P连接。

```C++
  // 创建一个放置信号远端的容器
  NodeContainer remoteHostContainer;
  // 创建remote_n个
  uint32_t remote_n = 2;
  remoteHostContainer.Create (remote_n);

  //TO Confirm remoteHost是从容器中获取第一个远端。
  Ptr<Node> remoteHost0 = remoteHostContainer.Get (0);
  Ptr<Node> remoteHost1 = remoteHostContainer.Get (1);

  std::cout <<"Remote Host Nums -> "<< remoteHostContainer.GetN() <<std::endl;
  std::cout <<"Remote Host 0 -> " << remoteHostContainer.Get (0) <<std::endl;
  std::cout <<"Remote Host 1 -> " << remoteHostContainer.Get (1) <<std::endl;
  
  // 初始化网络
  InternetStackHelper internet;
  // 根据远端容器建立网络internet
  internet.Install (remoteHostContainer);

  // 创建一个 PointToPointHelper p2ph以简化创建点对点网络
  PointToPointHelper p2ph;
  // 初始化相关参数，设置要传播到创建的每个 网络设备 的属性值。
  p2ph.SetDeviceAttribute ("DataRate", DataRateValue (DataRate ("100Gb/s")));
  p2ph.SetDeviceAttribute ("Mtu", UintegerValue (1500));
  p2ph.SetChannelAttribute ("Delay", TimeValue (MilliSeconds (10))); // 10ms 延时
  
  NetDeviceContainer internetDevices = p2ph.Install (remoteHost0, remoteHost1);
```



![image-20221020190505670](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020190505670.png)

### II. 创建几个enB或者UE

```C++
  NodeContainer ueNodes;
  NodeContainer enbNodes;
  ueNodes.Create (numNodePairs);
  enbNodes.Create (numNodePairs);

  // Install Mobility Model
  // 这里初始化了节点对的初始位置。
  Ptr<ListPositionAllocator> positionAlloc = CreateObject<ListPositionAllocator> ();
  for (uint16_t i = 0; i < 4; i++)
    {
      positionAlloc->Add (Vector (50 * i, 0, 0));
    }

  MobilityHelper mobility; // 设置选项，即使用什么定位方案以及分配什么移动模型,将助手应用到 NodeContainer 以定位节点并为其分配移动模型
  mobility.SetMobilityModel("ns3::ConstantPositionMobilityModel");
  //使用NS3 自带的位置初始化模型 MinX和MinY为初始位置，Delta X Delta Y 为节点之间的间距，Gridwidth为每行节点数目，layoutType为布局方式
  mobility.SetPositionAllocator (positionAlloc);
  mobility.Install(enbNodes);
  mobility.Install(ueNodes);

```



![image-20221020191243471](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020191243471.png)

### III. 创建一个核心网

首先我们要创建一个核心网：

```C++
  Ptr<PointToPointEpcHelper> epcHelper = CreateObject<PointToPointEpcHelper> ();
```

![image-20221020193132200](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020193132200.png)

他会创建上图一样的一个拥有三个节点的普通的核心网。

那么如何将核心网和UE连接呢？使用ltehelper去设置这个epc网络：

```C++
  lteHelper->SetEpcHelper (epcHelper);
```

![image-20221020193313753](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020193313753.png)

设置核心网后，他会自动与所有的enB基站进行连接。

### IV.设定pgw和sgw节点位置

同时，我们还可以给sgw以及pgw节点设定他们的位置

```C++
  MobilityHelper pos_EPC;  
  Ptr<ListPositionAllocator> pos_sgw_node = CreateObject<ListPositionAllocator> ();
  pos_sgw_node->Add(Vector (75, -20, 0));
  Ptr<ListPositionAllocator> pos_pgw_node = CreateObject<ListPositionAllocator> ();
  pos_pgw_node->Add(Vector (75, 50, 0));
  mobility.SetMobilityModel("ns3::ConstantPositionMobilityModel");
  mobility.SetPositionAllocator (pos_sgw_node);
  mobility.Install(sgw);
  mobility.SetPositionAllocator (pos_pgw_node);
  mobility.Install(pgw);
```

![image-20221020200538798](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020200538798.png)

==这边有一个扯淡的地方，就是他提供的设定位置的工具只能不断的AddVector进去，他不能进行修改，这十分的麻烦，同时初始化EPC中的另一个节点，猜测为RH的节点似乎很难获取到。==

## 还在研究！！