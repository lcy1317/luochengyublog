---
title: 树莓派安装FISCO-BCOS
date: 2021-11-18 21:56:22
tags: Tips
categories: FISCO
author: Lcy

---

# 树莓派安装FISCO-BCOS

参考文档：[FISCO BCOS 源码编译 — FISCO BCOS v2.7.2 文档 (fisco-bcos-documentation.readthedocs.io)](https://fisco-bcos-documentation.readthedocs.io/zh_CN/latest/docs/tutorial/compile.html)

```shell
# 拉取ubuntu镜像
docker pull ubuntu

# 启动容器
root@ubuntu:~# docker run -it ubuntu /bin/bash
root@35cfb23764c7:/# 

# 安装相关依赖
apt-get update

apt-get install -y sudo

sudo apt install -y g++ libssl-dev openssl cmake git build-essential autoconf texinfo flex patch bison libgmp-dev zlib1g-dev automake libtool # 安装gcc用于编译

# 克隆代码
git clone https://gitee.com/FISCO-BCOS/FISCO-BCOS.git -b master

# 编译代码
cd FISCO-BCOS
mkdir -p build && cd build
cmake -DARCH_NATIVE=on ..
# 高性能机器可添加-j4使用4核加速编译
make -j2

# 树莓派4B编译完成大概耗时2h左右

# 进入build_chain.sh的目录/FISCO-BCOS/tools
cd FISCO-BCOS
cd tools

# 使用脚本构建FISCO-BCOS链
bash build_chain.sh -l 127.0.0.1:4 -e /FISCO-BCOS/build/bin/fisco-bcos

# 后续和正常搭链一致

# FISCO-BCOS启停
bash nodes/127.0.0.1/start_all.sh
bash nodes/127.0.0.1/stop_all.sh
```

需要注意的地方：

- 编译后的二进制文件位置：FISCO-BCOS/build/bin/fisco-bcos
