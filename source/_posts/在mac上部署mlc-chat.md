---
title: 在mac上部署mlc-chat
date: 2023-05-03 17:49:54
tags: AI
categories: AI
author: Lcy
---

## Mlc-Chat部署

MLC LLM 是一种通用解决方案，它允许将任何语言模型本地部署在一组不同的硬件后端和本地应用程序上，此外还有一个高效的框架，供每个人进一步优化自己用例的模型性能。**一切都在本地运行，无需服务器支持，并通过手机和笔记本电脑上的本地 GPU 加速**

然后这个我试了一下在M2 的mac上部署，主要也只是测试一下能不能用，实际上就是能用，但只能用一点点，对话能力不够强，比较凑合，中文能力只支持繁体。挺辣的一个小模型。

这玩意官网的部署指导实测了非常顺利没有什么环境依赖的问题，只要有conda就好了：

```shell
# Create a new conda environment and activate the environment.
conda create -n mlc-chat
conda activate mlc-chat

# Install Git and Git-LFS, which is used for downloading the model weights
# from Hugging Face.
conda install git git-lfs

# Install the chat CLI app from Conda.
conda install -c mlc-ai -c conda-forge mlc-chat-nightly

# Create a directory, download the model weights from HuggingFace, and download the binary libraries
# from GitHub.
mkdir -p dist
git lfs install
git clone https://huggingface.co/mlc-ai/demo-vicuna-v1-7b-int3 dist/vicuna-v1-7b
git clone https://github.com/mlc-ai/binary-mlc-llm-libs.git dist/lib

# Enter this line and enjoy chatting with the bot running natively on your machine!
mlc_chat_cli
```



效果图：（注意要在创建的目录下运行，比如我是在`/AIGC/mlcchat`目录下运行哈（给自己备忘））

![image-20230503175658004](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20230503175658004.png)

## Reference

[开源 AI 聊天机器人 MLC LLM 发布](https://www.ithome.com/0/690/261.htm)

https://mlc.ai/mlc-llm/
