---
title: ubuntu安装ns3
date: 2022-07-04 15:04:18
tags: Study
categories: Titanium Tech
author: Lcy
---



## Step 1 下载ns-3.36.1

下载页链接：[ns-3.36 | ns-3 (nsnam.org)](https://www.nsnam.org/releases/ns-3-36/)

然后进行解压操作：

```shell
tar xjf ns-allinone-3.36.1.tar.bz2 
cd ns-allinone-3.36.1
```



不过我觉得官方说的的克隆仓库会更好：

```shell
git clone https://gitlab.com/nsnam/ns-3-dev.git
cd ns-3-dev
# 这里最好切换一下分支，可以切最新的，不过这里我就用3.36.1
git checkout -b ns-3.36.1
```

## Step 2 构建并测试ns3

注意要先安装cmake

```shell
apt install cmake
```

然后先注册并构建一波ns3

```shell
# 根据配置文件配置
./ns3 configure --enable-examples --enable-tests
# 再build ns3
./ns3 build
```

![image-20220704153427958](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704153427958.png)

开始测试ns3，测试脚本会检查各个工具是否正常。

```shell
# 运行test脚本
./test.py
```

![image-20220704153611169](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704153611169.png)

```shell
# 运行ns3的相关测试
./ns3 run first
./ns3 run "first --PrintHelp"
```

![image-20220704153655079](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704153655079.png)

至此ns3 安装完成

