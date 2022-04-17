---
title: DeFi Learning(七)
date: 2022-04-17 00:00:30
tags: Study
categories: DeFi
author: Lcy 
---

# Part Three: Deep Diving into DeFi

A reading note for 《How to DeFi Beginner》

## 第七章 去中心化的交易所（DEX）

DEX的两种类型：

1. 基于订单簿地DEX Order book-based DEX
2. 基于流动性池的DEX Liquidity pool-based DEX

DEX的局限性：

1. 较低的流动性：目前大多是交易还是在中心化的交易所上进行的。在CEX里面毕竟大家的交易量是比较大的，对应到DEX里面价差就会较大，买卖双方可能由较大损失。
2. 功能有限：中心化交易所包括许多高级交易功能，例如限价单、止损单、追踪止损等。大多数这些交易功能在 DEX 上不可用。一些 DEX现在提供限价单，从而提供更好的交易体验。然而，越来越多的 DEX 正在寻求引入这些高级交易功能，以更有效地与 CEX 竞争。
3. 区块链的互操作性：大多数DEX只允许交易者在同一个区块链生态系统内交换代币。例如，基于以太坊的DEX只允许用户交易以太坊和 ERC-20代币。它不允许交易者交易在Polkadot或Cosmos等其他区块链上发行的代币。 CEX允许用户轻松地在各种区块链上交易代币。正在努力构建**跨链 DEX**，未来，在 DEX  上跨多个区块链交易代币将成为可能。
4. 费用：随着DeFi的流行，这会导致以太坊网络的拥挤。以太坊交易量的增加，也就会相应的引起Gas的增加带来成本费用的上升。也就是高峰期的时候DEX上的交易大多是昂贵的交易，这在矿难或者大跌的时候是能够经常看到的，交易手续费大幅度上升。

### Uniswap

Uniswap 是一种基于以太坊的去中心化代币交换协议，允许直接交换代币，而无需使用中心化交易所。

**流动资金池**

流动性池是位于Uniswap智能合约上的代币储备，可供用户交换代币。例如，使用流动性储备中有100ETH和20,000DAI的ETHDAI交易对，想要使用DAI 购买ETH的用户可以向 Uniswap 智能合约发送 202.02DAI以获得1ETH 作为回报。交换完成后，流动资金池将剩下99ETH和20,202.02DAI。流动性池的准备金由流动性提供者提供，他们被激励获得 Uniswap 0.3% 交易费的相应费用。Uniswap上的每次代币交换都会收取此费用。

任何人都可以提供流动性资金。

**自动的商市机制 Automated Market Maker Mechanism**

资金池中资产的价格是使用Automated Market Maker(AMM) 算法确定的。AMM 的工作原理是根据池两侧的流动性计算。

用 100 ETH 和 20,000 DAI 的  ETH-DAI 流动性池示例。为了计算恒定乘积，Uniswap 会将这两个金额相乘。

![image-20220417140956310](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220417140956310.png)

AMM要求这个乘积保持不变。

![image-20220417143109793](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220417143109793.png)

所以换的越多费率越高。

想要尝试一下可以去[Uniswap](https://app.uniswap.org/)了解一波。

### DEX 聚合器

简单来说就是现在很多的DEX由自己的流动性资金池所以想要换的比较多的话就会面临较高的费率。而DEX聚合器就是自动将你想要换取的路由到多个DEX中，拆分掉你的大宗交易，以此来获得最有的价格。例如[1inch]( https://1inch.exchange/)就是一个DEX聚合器。
