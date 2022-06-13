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

## GoCV读取图片三通道[]float32

```go
package main

import (
 "gocv.io/x/gocv"
 "log"
 "math"
)

type Image []float32

func main() {
 imageFilePath := "../../data/Lena.png"
 originalMat := gocv.IMRead(imageFilePath, gocv.IMReadGrayScale)
 if originalMat.Empty() {
  log.Panic("Can not read image: " + imageFilePath)
  return
 }

 originalImage := originalMat.ToBytes()
 targetImage := make(Image, len(originalImage))
 for i := 0; i < len(targetImage); i++ {
  targetImage[i] = float32(originalImage[i]) / 255
 }

 targetImage.zeroAverageMatrix()
 log.Println(targetImage)

 targetImage.dispersionMatrix()
 log.Println(targetImage)
}

func (image *Image) zeroAverageMatrix() {
 average := image.average()

 for i := 0; i < len(*image); i++ {
  (*image)[i] = (*image)[i] - average
 }
}

func (image *Image) dispersionMatrix() {
 average := image.average()
 tempImage := image.clone()
 length := len(tempImage)

 for i := 0; i < length; i++ {
  tempImage[i] = float32(math.Pow(float64(tempImage[i]-average), 2))
 }

 sum := tempImage.sum()

 standardDeviation := sum / float32(length-1)

 for i := 0; i < length; i++ {
  (*image)[i] = (*image)[i] / standardDeviation
 }
}

func (image Image) sum() float32 {
 length := len(image)
 var sum float32 = 0
 for i := 0; i < length; i++ {
  sum = sum + image[i]
 }

 return sum
}

func (image Image) average() float32 {
 length := len(image)
 sum := image.sum()

 return sum / float32(length)
}

func (image Image) clone() Image {
 length := len(image)
 cloneImage := make([]float32, length)
 for i := 0; i < length; i++ {
  cloneImage[i] = image[i]
 }

 return cloneImage
}
```



## Reference 

[hybridgroup/gocv: Go package for computer vision using OpenCV 4 and beyond. (github.com)](https://github.com/hybridgroup/gocv)

https://zhuanlan.zhihu.com/p/428249664
