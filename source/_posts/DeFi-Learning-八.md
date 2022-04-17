---
title: DeFi Learning(八)
date: 2022-04-17 14:38:10
tags: Study
categories: DeFi
author: Lcy 
---

# Part Three: Deep Diving into DeFi

A reading note for 《How to DeFi Beginner》

## 第八章 去中心化的衍生品

衍生品是一种合约，其价值来自另一种标的资产，例如股票、商品、货币、指数、债券或利率。每种类型的衍生品，无论是期货、期权还是掉期，都有不同的用途，每个投资者出于各种原因购买或出售它们。投资者交易衍生品的一些原因是为了对冲标的资产的波动性、推测标的资产的方向移动或利用其持有的资产。衍生品风险极大，交易时必须具备强大的金融知识和策略。  DeFi 衍生品 Dapp 的市值为 58.2 亿美元，占 DeFi 生态系统的 8.2%。

这本书主要关注了Synthesix和Opyn两种衍生品协议

### Synthetix

Synthetix包含两个部分，一个是Synthetic Asset（Synths），一个是Synthetic.Exchange。

Synthetix资产是Synths，现在有两种不同的Synths：

- Normal Synths：与标的资产正相关
- Inverse Synths：与表弟资产负相关

一个Synths的例子是Synthetic Gold （sXAU），就是跟踪黄金的价格表现。反向Synths资产的例子是iBTC，跟踪的是BTC的反向价格表现。

> 以反向合成比特币（iBTC）为例。假设在创建时，比特币 (BTC) 的价格为 10,600 美元——这将是入场价格。如果比特币下跌 400 美元至 10,200  美元，则 iBTC Synth 将额外价值 400 美元，售价为 11,000 美元，去中心化衍生品也是如此。相反，如果比特币升至 11,000  美元，iBTC Synth 现在将价值 10,200 美元。

Synths 让交易者无需持有标的资产即可获得资产的价格敞口。与传统的黄金经纪公司相比，Synthetic Gold (sXAU)  允许交易者以更少的麻烦（无需注册、无需旅行、无需中间人等）参与市场。Synthsc还有另一个用途——它们可以在彼此之间无摩擦地进行交易，这意味着可以在  Synthetix.Exchange  上轻松地将合成黄金转换为合成日元、合成白银或合成比特币。这也意味着任何拥有以太坊钱包的人现在都可以开放访问任何现实世界的资产！

当前支持的资产可以去[List - Synthetix System Documentation](https://docs.synthetix.io/tokens/list/)查看

#### Index Synths

这是一篮子货币，可以理解为，指数。

#### Synthetic Exchange

Synthetix Exchange 是一个去中心化的交易平台，专为 SNX 和 Synths 的交易而设计。 Synthetix 交易所没有订单簿，也没有像  Uniswap 这样的流动资金池。 Synthetix Exchange  允许用户直接与保持持续充足流动性的智能合约进行交易，从而从理论上降低滑点或缺乏流动性的风险。由于用户购买的是合成合约而不是交易标的资产，因此用户最多可以购买系统中的抵押品总额，而不会影响合约的价格。



For more information or mining Synth:[Home | Synthetix Staking](https://staking.synthetix.io/)

### Opyn

Opyn 为资产价格波动提供保护，并为智能合约提供保险。用户可以获得以太坊 (ETH)、Wrapped Bitcoin (WBTC)、Yearn  Finance (YFI)、Uniswap (UNI)、DeFiPulseIndex (DPI) 以及 Compound (COMP) 上的 USDC 和  DAI 存款的保护。

除了智能合约失败之外，Opyn  还可以防范财务和管理风险等其他风险。 Opyn 通过利用金融衍生品（即期权）来做到这一点。

For more information：https://v1.opyn.co/#/
