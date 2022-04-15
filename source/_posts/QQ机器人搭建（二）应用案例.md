---
title: QQ机器人搭建（二）应用案例
date: 2022-04-04 21:19:34
tags: QQrobot
categories: QQRobot
---

# QQ robot 协助博客部署

## 博客工作流

说一下我的博客工作流吧，显然可以直接编辑服务器上的博客文件或者直接传到服务器上，但是这里可以提供一个robot的应用案例。

当前我的博客是在windows环境下构建的，使用了Hexo来进行博客的生成和部署，比较方便。由于这不是用wordpress等搭建的，Hexo是生成静态网页，所以对应的github上我建立了一个仓库用于存放博客的数据与代码，在本地更新博文。

更新一条博文大致如此：

- 更新一个Blog
- git push到github远端仓库
- 服务器对应目录git pull远端的改动

## Robot 可以干什么？

emm就是为了这个案例所以可以用部署在服务器上的robot来协助我完成远端的git pull操作，这样我就不用再去连接服务器操作了（虽然连一下并不麻烦。）

## Robot 程序

注：本程序基于旧版go-cqhttp，导入的库注意现在应该是nonebot.adapters.onebot.v11

```python
from nonebot import on_command,on_startswith
from nonebot.rule import to_me
from nonebot.adapters.cqhttp import Bot, Event, MessageSegment, Message
import os
import subprocess
from bs4 import BeautifulSoup
love = on_startswith(msg="更新博客", priority=2)

@love.handle()
async def love_rev(bot: Bot, event: Event, state: dict):
    p = subprocess.check_call(["git","pull"], cwd='/root/Desktop/luochengyu/HomePage/dist/lcyblog')
    if p == 0:
        await love.finish("博客更新完成！")
    else:
        await love.finish("拉取错误！")
```

## 实现效果

当给机器人发送<更新博客>命令后，robot将自动执行git pull命令并更新博客~

![image-20220404211659936](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220404211659936.png)
