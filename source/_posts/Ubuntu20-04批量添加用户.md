---
title: Ubuntu20.04批量添加用户
date: 2022-11-16 16:41:52
tags: Tips
categories: Tips
author: Lcy
---





网上有很多批量增加用户的方式，但是还是看到的有一个方式最为简单，也最为有效：

### （1）先编辑一个文本用户文件

首先创建一个文本文件：`serc.txt`

由于/etc/passwd中一行记录对应着一个用户，每行记录又被冒号(:)分隔为7个字段，其格式和具体含义如下：

```
用户名:口令:用户标识号:组标识号:注释性描述:主目录:登录Shell
```

要注意每个用户的用户名、UID、宿主目录都不可以相同，其中密码栏可以留做空白或输入x号，也可以设置统一初始密码。比如：

```shell
 user1:123456:800:100:user:/home/user1:/bin/bash
 user2:123456:801:100:user:/home/user2:/bin/bash
 user3:123456:802:100:user:/home/user3:/bin/bash
 user4:123456:802:100:user:/home/user4:/bin/bash
```

### （2）以root身份执行命令 `/usr/sbin/newusers`

从刚创建的用户文件`serc.txt`中导入数据，创建用户命令：

```
newusers < serc.txt
```

### （3）查看是否创建成功：

```
ls /home
```

### （4）权限修改：

通常权限可修改为700，所以：

```shell
chmod 700 user1
chmod 700 user2
chmod 700 user3
chmod 700 user4
```

### Reference

[Ubuntu 20.04下批量添加用户 - walden_yin - 博客园 (cnblogs.com)](https://www.cnblogs.com/Deskew/p/14469031.html)
