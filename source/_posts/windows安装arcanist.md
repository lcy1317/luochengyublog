---
title: windows安装arcanist
date: 2022-07-03 00:07:19
tags: Tips
categories: Useful Tools
author: Lcy
---

## Step 1 安装PHP

这是安装arcanist最讨厌的事情因为我被ubuntu的php坑过很多次，所以一看到要装php就头大，不过windows下php好像不会出什么离谱事情。

首先下载一个php：[PHP: Downloads](https://www.php.net/downloads.php)

将php的目录添加到环境变量：

![image-20220703002002616](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220703002002616.png)

在php目录下放置ini文件，可以下载我这个：

https://luochengyu.oss-cn-beijing.aliyuncs.com/php.ini

最后检查PHP版本：

![image-20220703001851716](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220703001851716.png)

## Step 2 安装ARC

克隆arc仓库以及一个我也不知道干嘛的东西：

```shell
git clone https://github.com/phacility/arcanist.git
git clone https://gitee.com/lzcspace/libphutil.git
```

然后一样添加环境变量

最后检查一下版本

![image-20220703002710645](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220703002710645.png)

OKay！
