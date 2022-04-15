---
title: QQ机器人搭建（一）
date: 2022-04-04 18:18:22
tags: QQrobot
categories: QQRobot
author: Lcy

---

# QA

## QQrobot用来干什么好？

A：显然QQ机器人被用来做一些简单的消息回复是最基础也是最无聊的工作，调用API查查天气和搜搜H图也是QQrobot的新手玩家部署在机器人上寻乐子的。而我在用了很久QQrobot后发现他更多的可以作为一个提供自动化执行操作的窗口，提供一些脚本化服务。

For Example：

- 健康日报，简化日报流程，直接让机器人发POST请求，也不用每天自己手动填写重复的信息。
- 青年大学习，青年大学习目前也是一个POST请求罢了，每周你只需要给自己的robot发个消息就完成，多是一件美事。
- 备忘，当然大部分时候专业的软件做这个比自己做好的多，但有些特异化功能可以自己实现。
- 球场预约
- ……

总之将QQrobot当成一个命令入口我觉得是当前QQrobot最大价值之一，而他的功能完全由自己编写。

## 用什么搭建QQ robot比较好？

A：个人推荐使用[NoneBot](https://v2.nonebot.dev/)+[OneBot](https://onebot.dev/)进行搭建，会更加简单也更加快速。

## 需要会什么？

A：只要会Python就可以。

