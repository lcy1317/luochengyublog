---
title: 在Pypi上上传Lcyutils包
date: 2022-05-19 16:42:49
tags: Tips
categories: Useful Tools
author: Lcy
---





最近写了一个自己的工具库，现在实现的是两个功能，一个是可以调用给我发邮件 ，另一个是通过1794957373的QQ号通过简单调用一个python函数来进行一个QQ消息的推送。

## lcyutils包

先来自我介绍一下自己的这个包，主要介绍一下QQ消息的反推功能。

当前仅仅在lcyutils.qqmessage模块里提供了一个消息的发送接口lcy_message

比如这样调用：

```python
import lcyutils.qqmessage as qq
qq.lcy_qqmessage(qq="1157***882就是你的QQ",message = "来一条测试消息~")
```

然后你就可以在QQ上接受到他给你发送的消息：

![image-20220520104023056](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220520104023056.png)

这个lcy_message函数有两个参数：

- qq：你接受消息推送的QQ号
- message：你想要发送的消息，一个string格式的字符串

## QQ消息推送的实现

这个实现其实毕竟利用到了QQ机器人，所以借助了我在服务器上跑的一个QQ机器人。

![image-20220529011909893](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220529011909893.png)

大致是这样一个流程，主要使用了go-cqhttp协议。

## TODO:

显然这里呢有一系列的问题，不管是传包时候的问题还是我自己写包时候的问题都有很多问题。这里总结一下希望有空能够一个个fix：

- pypi上的包的setup没有处理过包依赖的问题（Fixed）
- 设置消息token/转移后端端口（未解决）
- qqmessage支持更多的消息格式，图片/文件等（未解决，已更新链接图片发送）
- 包的结构需要调整，以及需要调整git的流程保证我这边开发和github以及包生成的一致性（未解决）
- 支持更多的工具（未解决）

## 上传

### setup编写

```python
#!/usr/bin/env python
# coding=utf-8

from distutils.core import setup
from setuptools import find_packages

with open("README.md", "r",encoding="utf-8") as f:
  long_description = f.read()

setup(
    name="lcyutils",   # python包的名字
    version="0.0.3",                # 版本号
    description='LCY Personal Tools',           # 描述
    long_description=long_description,                  # 详细描述，这里将readme的内容放置于此
    author='luochengyu',                                      # 作者
    author_email='luochengyu1317@163.com',              # 作者邮箱
    maintainer='luochengyu',                               # 维护人
    maintainer_email='luochengyu1317@163.com',       # 维护人邮箱
    license='MIT License',                                    # 遵守协议
    packages=find_packages(),
    install_requires=[                                               # lamb-common依赖的第三方库
      'requests>=2.26.0',
    ],
    platforms=["all"],                                                # 支持的平台
    url='https://github.com/lcy1317/lcytools',          # github代码仓地址
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',    #对python的最低版本要求
)
```



根据setup.py生成包

```shell
python setup.py sdist bdist_wheel
```

上传

```shell
twine upload dist/*
```

安装

```shell
pip install lcyutils==0.0.3 -i https://pypi.python.org/simple
```

