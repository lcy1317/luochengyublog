---
title: Git 使用系统代理
date: 2022-04-05 18:13:42
tags: Tips
---

# Git 使用系统代理

```shell
git config --global http.proxy 'http://127.0.0.1:1080'
git config --global https.proxy 'https://127.0.0.1:1080'
```

其中端口号为代理软件中配置的端口，如：

![image-20220405181526848](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220405181526848.png)
