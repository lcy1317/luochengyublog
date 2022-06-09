---
title: ubuntu 安装科学上网
date: 2022-06-09 23:03:07
tags: Tips
categories: Tips
author: Lcy
---

## 1.安装ShadowSocks

```shell
apt-get install python3-pip
apt install libsodium-dev
pip install https://github.com/shadowsocks/shadowsocks/archive/master.zip -U
```

## 2.ShadowSocks配置

### 找到ShadowSocks的安装位置

```shell
find / -name shadows*
```

### 在安装路径下新建并修改默认配置文件

```shell
sudo vim config.json
```

并写入如下内容

```
{  "server":"*****",  "server_port":*****,  "local_port":1080,  "password":"*****",  "timeout":600,  "method":"chacha20-ietf-poly1305"  }
```

其中server、server_port、password处需要分别替换为你购买的服务器网址、端口和密码。

确定上面的配置文件没有问题，即可在终端输入如下命令以启动ShadowSocks。

```shell
sslocal
```

## 3. 开机启动

修改rc.local文件

```shell
cd /etc
vim rc.local
```

添加一行

```shell
/usr/local/bin/sslocal -c /usr/local/lib/python3.8/dist-packages/shadowsocks/config.json
```

注意后面的要是你自己的shadowsocks路径

经过上面的配置，只是启动了sslocal，但是要上网，还需要配置浏览器到指定代理端口，如1080，才可以正式上网。

## 4. 配置浏览器

### 安装插件

我们需要给chrome安装SwitchyOmega插件，但是没有代理之前是不能从谷歌商店安装这个插件的，但是我们可以从Github上直接下载最新版 https://github.com/FelisCatus/SwitchyOmega/releases/ （这个是chrome的）然后浏览器地址打开chrome://extensions/，将下载的插件托进去安装。

## 5.Git使用代理

```shell
git config --global http.proxy socks5://127.0.0.1:1080
git config --global https.proxy socks5://127.0.0.1:1080
```

