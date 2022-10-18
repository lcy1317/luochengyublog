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
