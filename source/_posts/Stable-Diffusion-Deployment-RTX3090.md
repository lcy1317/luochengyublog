---
title: Stable Diffusion Deployment(RTX3090)
date: 2022-09-11 14:17:02
tags: Study
categories: Study
author: Lcy
---

# Stable Diffusion AI 作画本地部署

[toc]

## 1. 环境准备

首先去Stable Diffusion的仓库下载代码并配置相应的conda环境。

代码仓库：[CompVis/stable-diffusion (github.com)](https://github.com/CompVis/stable-diffusion)

环境配置可以参考官方库提供的方法：

```shell
conda env create -f environment.yaml
conda activate ldm
```

同时升级最新的latent diffusion可以：

```shell
conda install pytorch torchvision -c pytorch
pip install transformers==4.19.2 diffusers invisible-watermark
pip install -e .
```

## 新活来了 断更！

部署了Novel AI 但是AI能画色图所以。。。。。Whatever ai.seujyh.cn提供给大家，但是可能绝大部分时间都是关掉的，避免出现法律问题