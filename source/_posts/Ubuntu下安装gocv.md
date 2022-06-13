---
title: Ubuntu下安装gocv
date: 2022-06-13 16:04:39
tags: Tips
categories: Tips
author: Lcy
---

## Ubuntu 安装指导

当前的仓库要求的还是安装opencv4.6

gocv想要用就必须使用make进行编译。

### Step1 克隆仓库

```shell
git clone https://github.com/hybridgroup/gocv.git
```

![image-20220613161028219](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220613161028219.png)

### Step2 make install

Once you have cloned the repo, the following commands should do everything to download and install OpenCV 4.6.0 on Linux:

```shell
cd gocv
make install
```

If you need static opencv libraries

```shell
make install BUILD_SHARED_LIBS=OFF
```

![image-20220613162328973](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220613162328973.png)

看到gocv和opencvlib的版本信息就编译完成了

### Step3 测试Gocv读取文件

```go
package main

import (
	"gocv.io/x/gocv"
)

func main() {
	image := gocv.IMRead("./test.png", gocv.IMReadColor)
	//构建窗口
	window := gocv.NewWindow("img")
	window.ResizeWindow(500, 300)

	//在窗口展示图片
	window.IMShow(image)
	window.WaitKey(0)
	window.Close()
}
```

## Reference 

[hybridgroup/gocv: Go package for computer vision using OpenCV 4 and beyond. (github.com)](https://github.com/hybridgroup/gocv)
