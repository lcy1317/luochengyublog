---
title: DeFi Learning(十二)
date: 2022-04-17 23:40:07
tags: Study
categories: DeFi
author: Lcy
---

# Part Three: Deep Diving into DeFi

A reading note for 《How to DeFi Beginner》

## 第十二章 去中心化保险

参与DeFi的过程中，必须将代币锁定在智能合约中，但是显然即使是审计过的智能合约也有可能存在缺陷而被黑客攻击。所以就有了去中心化的保险。

所以使用DeFi必须要面对：

1. 技术风险：智能合约可能被黑客攻击或漏洞被利用
2. 流动性风险：借贷协议（如 Compound）可能耗尽流动性
3. 管理密钥风险：协议的公私钥可能被泄露

###  Nexus Mutual

Nexus Mutual  是建立在以太坊上的去中心化保险协议，为以太坊区块链上的智能合约提供保障，并为中心化贷方和交易所（如Celsius、Blockfi、Nexo、Binance、Coinbase、Kraken  和 Gemini）提供托管保障。

保险的保护范围是智能合约的意外，如果只是自己丢了私钥那没救了。

NXM是Nexus Mutual的原生代币

[Nexus Mutual | A decentralised alternative to insurance](https://nexusmutual.io/)

### Armor

Armor  是 DeFi 的第一个保险聚合器。利用 Nexus Mutual 的承保能力，它提供现收现付保险产品以及无需 KYC 即可购买保险的能力。不想进行 KYC 或因 Nexus Mutual 的地域限制无法购买保险的用户可以通过 Armor 获得保险。

[Armor.Fi](https://armor.fi/)

### Nsure Network

Nsure Network  是一个去中心化的保险项目，它借鉴了伦敦劳合社的理念，这是一个交易保险风险的市场。保费价格使用动态定价模型确定，其中资本供需共同决定保费，类似于自由市场的定价机制。

Nsure  Network 的治理代币 (NSURE) 由购买的政策支持。价格可根据资本供求的变动自行调整，但受基础模型的稳定。与遵循互惠模式的 Nexus Mutual  不同，Nsure Network 遵循股东模式，其中 Nsure Network 的代币类似于持有网络的一部分。

### Cover Protocol

Cover Protocol 是一个点对点保险市场，其运作类似于预测市场。与其他保险协议不同，治理代币不用于承保风险。为了引导这一新协议的覆盖范围，做市商被激励将  DAI 或 yDAI 抵押品用于铸造 CLAIM 和 NOCLAIM 代币。 Cover Protocol  保险涵盖选定的协议，并且都有指定的到期日。在到期日期间，CLAIM 或 NOCLAIM 代币将拥有抵押品的全部权利。

例如，如果在设定的到期日之前使用 100 DAI 为 Compound 协议提供保障，它将产生 100 CLAIM 和 100 NOCLAIM  代币。在到期日，如果有有效的索赔事件，所有 CLAIM 代币将获得 1 DAI，而所有 NOCLAIM 代币将一文不值。相反，如果没有有效的索赔事件，所有  NOCLAIM 代币将收到 1 DAI，而所有 CLAIM 代币到期时一文不值。要获得价值 100 DAI 的保险，用户需要从交易所购买 100 CLAIM  代币，因为如果发生有效索赔，这将过期至 100 DAI。购买 100 个 CLAIM 代币的成本将是保险费。



**Conclusion**

保险在 DeFi  中仍然是一个非常小众的细分市场，通常吸引的零售市场参与者很少。然而，随着更成熟的参与者加入市场，他们无疑将需要更好的风险管理工具。归根结底，投保或不投保的选择最终取决于您。但是，我们  CoinGecko 肯定会推荐购买保险，因为在 DeFi 中任何事情都可能发生。
