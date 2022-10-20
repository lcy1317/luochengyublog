---
title: XRDP 安装注意事项
date: 2022-10-20 18:31:21
tags: Tips
categories: Tips
author: Lcy
---
# XRDP 安装注意事项
## XRdp 安装

[如何在Ubuntu 20.04 上安装 Xrdp 服务器（远程桌面）-阿里云开发者社区 (aliyun.com)](https://developer.aliyun.com/article/762186)

```shell
sudo apt install xubuntu-desktop
```

## XRdp 设置允许root登录

修改配置文件：

```shell
vim /etc/xdrp/startwm.sh
```



![image-20221020183421120](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20221020183421120.png)

如图位置增加如下两句话：

```shell
unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
```

重启xrdp服务

```shell
systemctl restart xrdp.service
```

