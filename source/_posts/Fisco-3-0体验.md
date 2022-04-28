---
title: Fisco 3.0体验
date: 2022-04-28 21:51:55
tags: Study
categories: FISCO
author: Lcy
---

# Ubuntu Fisco 3.0 体验

Fisco 3.0 发布了，准备着本地去搭建一个Fisco3.0的链，同时试验一下2.0的go sdk是否能用，如果不能用的话短期业务就不能切到3.0去开发。

## 本地搭链

在对应文件夹里终端执行：

```shell
# 下载脚本
curl -#LO https://osp-1257653870.cos.ap-guangzhou.myqcloud.com/FISCO-BCOS/FISCO-BCOS/releases/v3.0.0-rc3/build_chain.sh && chmod u+x build_chain.sh
# 脚本建链
bash build_chain.sh -l 127.0.0.1:4 -p 30300,20200
```

![image-20220428215623117](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220428215623117.png)

## 使用GO SDK

好了不用尝试旧的了，配置文件以及一系列的证书设置都全新了。

太草，Fisco 3.0的SDK更新太慢了。
