---
title: 写第一篇paper的一些记录
date: 2022-08-01 23:45:11
tags: Study
categories: Study
author: Lcy
---

# 1. 万恶之源

这都怪7.15的时候，老板在我跑步刚刚结束还搁那大喘气呢，来了一个电话，上来第一句：

> 你太不上进了！

我快速反思了一下最近干了什么，0.5s之后反应过来肯定是有话要说虚晃一枪，而后果然就：

> WCSP你投一下，7.30截稿，把毕设写成论文，下周给我初稿。

虽然吧是个三区的会议但是对我这种废物菜鸡躺平人士来说，我真的我也不会写论文啊，但是也就嗯啊嗯下来了，所以度过了痛苦的两周。

# 2. 踩坑

时间毕竟是紧迫的，所以写论文的过程中遇到了一系列的问题，我来回想回想来一下一一列举。

## a. 正文

首先是按照写作的顺序，从正文开始写作。对于正文的写作还是要先深入理清楚整体的思路。时间紧所以我就按照毕设里的思路一通瞎写，又因为毕设的东西太多，会议的篇幅也不够表述，删删减减之中逻辑就丢失掉了。所以要注意这么些个事情：

### 1.意识流地表述因果关系、转折关系、承接关系
（这个错误大多数中文使用者都能发现）

写文章的时候写着写着就一定程度上丢了一些逻辑，比如想着A，但A还没写完就写到B；又比如想着从A转折到B，结果写着写着就顺着写下去了，忘了加转折关系。最后呈现出来的感觉就是不断地跳变。

所以这就要求在写paper的时候不要赶时间，（大佬除外），每一句话写的时候深入思考一下，一点点的写一写。

### 2.主谓语搭配错误，of/in/with/on等介词使用错误
（这个大多是由中式思维引发）

介词这个其实是小问题，毕竟写完论文去过Grammarly还是非常的快速的，过Grammarly的同时学一下一些表述也问题不大。

### 3.表述过冗余
（需要摆脱口语化思维，尽量压迫自己在每句话开头说点有用的话，先不要在句子里加过多定语、副词，先把核心意思写出来）

这个乐博给了一个要求，在每一句的前6个词最好出现一点实际的东西。比如我这篇文章在写的时候经常写到了一些什么`Therefore, it is able to `这样上来5个词全在说废话，Reviewer就会发现看不见这句话想要表达什么，所以不要在每一句话的开头说太多的废话。

## b. Simulation

### 1.冗余的繁杂表述

（每段的开头可以不用讲述废话，直接使用Fig. ? shows that之类的句式进行说明）

一开始写仿真描述的时候，写了很多的废话，尤其是在叙述仿真结果的过程中应当避免讲故事，将缘由等等一些无关的事情。就应当聚焦于要写的内容，需要描述的变化趋势进行描述。

## c. Introduction

首先注意常见的标准Intro的5个点：

1. 一个引入，引入要做的工作
2. 介绍相关领域的工作，做一个简单的literature research。
3. 介绍当前工作的一些缺点
4. 介绍自身工作的贡献
5. 介绍后面文章的结构

### 1. literature research过于冗长

首先文献调研的内容不需要过于长，通常对于一篇文献来说的对应的对于其的总结性陈述在2行左右即可。

### 2. 缺点以及贡献陈述

这里要注意缺点和贡献的陈述通常需要一一对应，有什么样的缺点，我们文章的贡献点又在哪里，我们提出的方案到底带来了什么，一一对应更能体现工作的价值所在。

## d. Conclusion

### 1. 再一次陈述核心的贡献

总结全文的贡献，清晰明了的陈述核心的贡献点。

有时候看篇幅的控制，可以再加上对未来的展望。

## e. Abstract

### 1. 及时cue文章Title

对于Ab来说，通常在前六行一定要注意cue到我们所需要做的事情，cue到title。如果文章涉及的要素过多，ab开头不方便一一介绍，需要想想有什么总结性的介绍方式快速的展开cue到title。

## f. Ref

### 1. 条目的润湿

（一定不能忘）

几个很重要的点需要mark不能忘记：

1. 在bib文件中过一遍所有文章的标题中需要强制大写的内容，比如IoT、6G等需要用大括号来强制大写
2. 过一遍所有的会议，补充**会议月份、会议地点**，改写会议的名字格式**注意补充届数，在前面写上Proc等细节**
3. 过一遍所有的会议和期刊，对相应的会议名、期刊名找缩写进行修改。参考网站：[Science and Engineering Journal Abbreviations | Woodward Library (ubc.ca)](https://woodward.library.ubc.ca/research-help/journal-abbreviations/)
