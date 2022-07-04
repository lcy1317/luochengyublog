---
title: ubuntu设置root登陆
date: 2022-07-04 14:02:04
tags: Tips
categories: Useful Tools
author: Lcy
---

## Step 1 给root用户设置账户密码

```shell
sudo passwd root
# 切换用户
su root
```

## Step 2 修改gdm-autologin文件

```shell
vim /etc/pam.d/gdm-autologin
```

注释掉：`auth required pam_succeed_if.so user != root quiet_success`

![image-20220704143736406](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704143736406.png)

## Step 3 修改gdm-password文件

```shell 
vim /etc/pam.d/gdm-password
```

注释掉：`auth required pam_succeed_if.so user != root quiet_success`

![image-20220704143811079](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704143811079.png)

## Step 4 修改/root/.profile文件

```shell
vim /root/.profile
```

注释掉：`mesg n 2> /dev/null || true`

并追加一行：`tty -s&&mesg n || true`

![image-20220704143845212](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220704143845212.png)

## Step 5 重启

```shell
reboot
```

