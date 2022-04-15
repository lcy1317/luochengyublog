---
title: 使用Typora的PicGo-Core配置阿里云OSS图床
date: 2022-03-09 16:38:51
tags: Tools
categories: Useful Tools
---

最近遇到一个比较苟的事情，PicGo可以成功的上传文件，Typora也能够自动调用PicGo，但是PicGo上传完文件后无法将链接返回，直接卡死，所以准备换PicGo-Core来配置图床。

1. 选择PicGo-Core

![image-20220309163258640](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/875dbfdcdce0f11684812f1627d1c5aa.png)

2. 如果没有用过PicGo-Core先点击一下==下载或更新==
3. 设置PicGo-Core的配置文件，下面给出阿里云的图床配置Config配置：

```json
{
  "picBed": {
    "uploader": "aliyun",
    "aliyun": {
      "accessKeyId": "必填",
      "accessKeySecret": "必填",
      "area": "必填，如oss-cn-beijing",
      "bucket": "必填",
      "customUrl": "",
      "options": "",
      "path": "img/"
    }
  },
  "picgoPlugins": {}
}
```

4. 验证图片上传选项

![image-20220309163605968](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/8166478047f1e582848554b7f6d8c26a.png)



验证成功即可~
