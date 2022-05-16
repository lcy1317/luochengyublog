---
title: ubuntu 安装anaconda配置python环境
date: 2022-05-16 22:06:48
tags: Tips
categories: Tips
author: Lcy
---

# Ubuntu 安装anaconda

## 1.下载anaconda

直接使用清华源下载anaconda

```shell
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-2022.05-Linux-x86_64.sh
```

## 2. 安装anaconda

```shell
bash Anaconda3-2022.05-Linux-x86_64.sh
source ~/.bashrc
conda --version
```

<img src="https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220516230009483.png" alt="image-20220516230009483" style="zoom:90%;" />

## 3. 新建一个conda环境（可选）

```shell
conda create -n bot python==3.9
```

# 常用conda命令

```shell
#创建虚拟环境
conda create -n your_env_name python=X.X（3.6、3.7等）
 
#激活虚拟环境
source activate your_env_name(虚拟环境名称)
 
#退出虚拟环境
source deactivate your_env_name(虚拟环境名称)
 
#删除虚拟环境
conda remove -n your_env_name(虚拟环境名称) --all
 
#查看安装了哪些包
conda list
 
#安装包
conda install package_name(包名)
conda install scrapy==1.3 # 安装指定版本的包
conda install -n 环境名 包名 # 在conda指定的某个环境中安装包
 
#查看当前存在哪些虚拟环境
conda env list 
#或 
conda info -e
#或
conda info --envs
 
#检查更新当前conda
conda update conda
 
#更新anaconda
conda update anaconda
 
#更新所有库
conda update --all
 
#更新python
conda update python
```

# Reference

[Ubuntu 安装 conda - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/459607806#:~:text=安装Anaconda (Linux%2FUbuntu) 1 安装Anaconda首先先得到权限，然后再使用sh进行安装。 sudo chown,-R henchli Anaconda3-2020.07-Linux-x86_64.sh sudo sh Anaconda3-2020.07-Linux-x86_64.sh按着enter看完简介之后，输…)
