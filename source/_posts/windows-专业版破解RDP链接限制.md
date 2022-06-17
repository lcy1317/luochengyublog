---
title: windows 专业版破解RDP链接限制
date: 2022-06-18 00:11:51
tags: Tips
categories: Tips
author: Lcy
---

# Windows 10 破解RDP 连接限制

## I.几个有用的链接：

1. 适用于20H2版本的破解文件：https://github.com/sebaxakerhtc/rdpwrap.ini
2. RDP Wrap 的官方github仓库：https://github.com/stascorp/rdpwrap/issues需要在issue中找新版本的破解文件
3. 一个比较有用的破解的博客：https://www.cnblogs.com/JvYouQing/p/15539004.html
4. 我打包好的文件：https://luochengyu.oss-cn-beijing.aliyuncs.com/useful/RDPWrap-v1.6.2.zip?versionId=CAEQIhiBgMC48vDJixgiIDQ2YjQwYzk5YmQzYzRmYWI5Njk5YTU0NzNiMTc0MTI0

## II. How to 破解

创建账户等等一系列的操作就不想要赘述了。参考上面第三个的链接可以搞定，或者网上能搜到一堆的教程。

解压链接4中给的文件：

![image-20220618002512849](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220618002512849.png)

按照如下顺序依次运行：

1. install.bat
2. update.bat
3. RDPConf.exe

如果RDPConf.exe运行完如下图所示：

![image-20220618002634553](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220618002634553.png)

如果是full supported那就是破解完成重启就好。

如果没有，那就把链接1中的文件（[rdpwrap.ini](https://luochengyu.oss-cn-beijing.aliyuncs.com/useful/rdpwrap.ini?versionId=CAEQIhiBgMCJ.prKixgiIDhiY2FkMDEwYjNhMTQ2MmM5OTU4OGNhNDZjOGRkODFi)）放到C:\Program Files\RDP Wrapper目录下。

之后重复运行上述几个文件，就能看到fully supported的字样了

然后重启！
