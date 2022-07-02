---
title: windows安装hexo
date: 2022-07-02 23:37:50
tags: Tips
categories: Useful Tools
author: Lcy
---



## Step 1 npm安装

如已安装npm可以跳过本步骤。

在[nodejs官网](https://nodejs.org/en)上下载nodejs

![image-20220702233942774](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220702233942774.png)

一路next安装下去并检查：

```shell
# 查看系统的环境变量
echo %PATH%
node -v
```

![image-20220702234348161](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220702234348161.png)

如上图所示即为安装成功。

如果需要配置自定义镜像提升速度，可以为NodeJS配置自定义的镜像，命令如下：

```shell
npm config set registry=http://registry.npm.taobao.org
```

检查配置信息

```shell
npm config list
```

![image-20220702234645238](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220702234645238.png)

```shell
npm config get registry
```

## Step 2 安装hexo

```shell
npm install hexo-cli -g
```

![image-20220702235057643](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220702235057643.png)

然后测试一下hexo g & hexo s是否能生成博客就行了。

