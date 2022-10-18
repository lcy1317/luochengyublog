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

