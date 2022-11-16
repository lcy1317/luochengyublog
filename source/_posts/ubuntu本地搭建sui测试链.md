---
title: ubuntu本地搭建sui测试链
date: 2022-10-25 10:16:43
tags: Study
categories: Study
author: Lcy
---

 sui官网：[Install Sui to Build | Sui Docs](https://docs.sui.io/build/install)

如果看官网觉得麻烦那就按照如下的命令直接运行就ok了：

```shell
# 更新源
apt update
apt upgrade

# 安装curl
apt install curl

# 安装rust & cargo
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# 安装libssl-dev
apt-get install libssl-dev

# 安装libclang-dev
apt-get install libclang-dev

# 安装sui 
cargo install --locked --git https://github.com/MystenLabs/sui.git --branch devnet sui sui-node

```

