---
title: 使用nps替代向日葵
date: 2022-05-04 00:48:53
tags: Tips
categories: Useful Tools
author: Lcy
---

# Nps替代ToDesk、向日葵、TV的解决方案

## 1. TV/向日葵痛点

常用TV以及向日葵的同学知道，这俩好用是挺好用，但是有一些问题是很讨厌的。比如：

- 远程登陆后本地的机子还是能看见屏幕上的操作
- 多终端的适配不合适
- 可能会限制终端数量

然而Nps可以解决所有这些问题，并且他利用了微软自己的远程桌面，分辨率可以做到自适应你的屏幕，双屏？异形？手机？平板？都可以用来作远程，毫无问题。把平板变成电脑也是简简单单的事情。

如何搭建自己的远程桌面呢？

## 2. 拥有一台自己的公网服务器

本来应该不会出现这个教程的，但是偶然看到了百度云作活动，139可以买到两年的轻量应用服务器，又是忍不住就去买了，服务器这玩意么，能干的事情太多了，139和白送没有区别！

如下图：

![image-20220504005637064](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504005637064.png)

点击注册[百度智能云](https://console.bce.baidu.com/qualify/#/qualify/index?invitationUserCode=fmwTG6KE&campaignId=20220407_discount_time)，其实之前阿里云也有更香的但是活动早没了，薅不到了。

当然如果你没有云服务器的需求，单纯想要一个非常好用的远程桌面，可以买左边更便宜的39/年的或者找我代为开个远程连接，可以给个很便宜的价格，也不用自己折腾服务器哈哈。

## 3. 安装一下nps的server端

本来打算说吧用docker安装，但是这边拉docker的东西有点慢，算了，直接下release来安装好了

查看所有release可以去[Releases · ehang-io/nps (github.com)](https://github.com/ehang-io/nps/releases)

在你自己的某个文件夹下做这个操作，比如/root/nps/

```shell
# 下载文件
wget https://github.com/ehang-io/nps/releases/download/v0.26.10/linux_amd64_server.tar.gz

# 解压文件
tar -xvf linux_amd64_server.tar.gz
```

之后你会看到这些文件：

![image-20220504012031633](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504012031633.png)

在conf文件夹下的nps.conf文件夹下可以进行一些配置的更改：

详细配置含义如图：

<img src="https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504012244835.png" alt="image-20220504012244835" style="zoom:50%;" />

主要你需要更改的信息如下：

![image-20220504012618804](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504012618804.png)

至于修改用vim/xftp咋修改都行。

此后执行:

```shell
./nps install
nps start
```

nps就可以在制定端口开启一个前端的控制界面，可以在上面进行可视化操作了。

![image-20220504013153041](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504013153041.png)

登陆后如图：

![image-20220504013224729](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504013224729.png)

## 4. 配置client客户端

首先在管理界面里进行一个客户端新增

![image-20220504014950059](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504014950059.png)

请记住你的**唯一验证密钥**。

![image-20220504020946893](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504020946893.png)

同时，新建一个tcp隧道：

![image-20220504022156187](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504022156187.png)

注意这里的客户端ID与上图中的ID保持一致。

windows可在[下载链接](https://github.com/ehang-io/nps/releases/download/v0.26.10/windows_amd64_client.tar.gz)下载client或者找合适的release自行下载。

解压文件并以管理员身份运行cmd

![image-20220504021103309](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504021103309.png)

输入`npc.exe -server=你的服务器ip+客户端连接端口 -vkey=你设置的唯一密钥 -type=tcp`

![image-20220504021308980](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504021308980.png)

至此全部配置完毕。

## 5. 连接

windows电脑连接直接使用电脑自带的远程桌面连接即可，这里的端口号就是你在配置TCP隧道时候自己设置的服务端口：

![image-20220504021455286](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504021455286.png)

手机平板等下载RDclient进行连接即可。

![image-20220504021550909](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220504021550909.png)

## Tips

肯定有人问80和443端口为什么被占用了，这个不用担心，默认配置用的是这俩端口，可以配合nginx进行更改的，有这个烦恼的看下文档也知道怎么弄了。

# Reference

[取代Teamviewer：NPS内网穿透小教程 - 硬核小站 (exhard.cn)](http://exhard.cn/wordpress/?p=324)
