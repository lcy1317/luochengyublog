---
title: QQ机器人搭建（三）环境构建
date: 2022-05-16 23:53:45
tags: QQrobot
categories: QQRobot
author: Lcy
---

# QQrobot 环境搭建

## 1. 安装nonebot2

```shell
pip install nonebot2
# 安装nonebot脚手架
pip install nb-cli
```

## 2. 安装go-cqhttp

[go-cqhttp 帮助中心](https://docs.go-cqhttp.org/)

下载最新发行版

```shell
wget https://github.com/Mrs4s/go-cqhttp/releases/download/v1.0.0-rc1/go-cqhttp_1.0.0-rc1_linux_amd64.deb
# 安装
dpkg -i go-cqhttp_1.0.0-rc1_linux_amd64.deb
# 启动
go-cqhttp
```

![image-20220517000405670](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220517000405670.png)

如图选择023就够用了

<font color= red>未完</font>

## 3. 修改config.yaml

后半部分参考配置

```json
# 连接服务列表
servers:
  # 添加方式，同一连接方式可添加多个，具体配置说明请查看文档
  #- http: # http 通信
  #- ws:   # 正向 Websocket
  #- ws-reverse: # 反向 Websocket
  #- pprof: #性能分析服务器

  - http: # HTTP 通信设置
      host: 127.0.0.1 # 服务端监听地址
      port: 5700      # 服务端监听端口
      timeout: 5      # 反向 HTTP 超时时间, 单位秒，<5 时将被忽略
      long-polling:   # 长轮询拓展
        enabled: false       # 是否开启
        max-queue-size: 0 # 消息队列大小，0 表示不限制队列大小，谨慎使用
      middlewares:
        <<: *default # 引用默认中间件
      post:           # 反向HTTP POST地址列表
      #- url: ''                # 地址
      #  secret: ''             # 密钥
	  #  max-retries: 3         # 最大重试，0 时禁用
      #  retries-interval: 1500 # 重试时间，单位毫秒，0 时立即
      #- url: http://127.0.0.1:5701/ # 地址
      #  secret: ''                  # 密钥
	  #  max-retries: 10             # 最大重试，0 时禁用
      #  retries-interval: 1000      # 重试时间，单位毫秒，0 时立即
  # 正向WS设置
  - ws:
      # 正向WS服务器监听地址
      host: 127.0.0.1
      # 正向WS服务器监听端口
      port: 6700
      middlewares:
        <<: *default # 引用默认中间件
  # 反向WS设置
  - ws-reverse:
      # 反向WS Universal 地址
      # 注意 设置了此项地址后下面两项将会被忽略
      universal: ws://127.0.0.1:9191/onebot/v11/ws
      # 反向WS API 地址
      api: 
      # 反向WS Event 地址
      event: 
      # 重连间隔 单位毫秒
      reconnect-interval: 3000
      middlewares:
        <<: *default # 引用默认中间件
```

<font color= red>未完</font>
