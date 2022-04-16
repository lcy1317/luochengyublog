---
title: DeFi Learning(六)
date: 2022-04-16 21:32:17
tags: Study
categories: DeFi
author: Lcy 
---

# Part Three: Deep Diving into DeFi

A reading note for 《How to DeFi Beginner》

## 第六章 去中心化的借贷

在 DeFi 环境中，也就是一个去中心化的环境下，并没有银行，所以没有法律、门槛、融资标准等等一系列的繁琐的东西。只要有足够的抵押物就可以获得贷款资金来做自己想做的事情。

这本书介绍了Compound和Avae两种比较牛逼的DeFi借贷协议。

### Compound

Compound Finance 是一种基于以太坊的开源货币市场协议，任何人都可以无摩擦地借出或借入加密货币。

现在在[Compound平台上](https://compound.finance/markets)已经有20中可以借贷的加密货币。

> Compound作为建立在以太坊区块链上的流动资金池运作。供应商向流动性池提供资产以赚取利息，而借款人从流动性池中获得贷款并支付债务利息。从本质上讲，Compound弥合了希望从闲置资金中累积利息的贷方和希望借入资金用于生产或投资用途的借款人之间的差距。在 Compound 中，利率以**年收益率 (APY)**  表示，并且资产之间的利率不同。 Compound 通过考虑资产供需的算法得出利率。从本质上讲，Compound  允许供应商/借款人直接与利率协议交互，而无需协商贷款条款（例如：到期日、利率、抵押品等），从而降低了借贷的摩擦，从而创建了一个更有效的货币市场.

以当前的行情来看，给一下平台上借贷双方能获得/需支付的利息年利率APY：

![image-20220416214703265](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416214703265.png)

#### Compound的管理

Compound已经越来越去中心化了，实际上提出治理提案的人需要有超过1%的总共的COMP（Compound的币，1%就是10W个COMP）进行委托，进入治理的Alpha阶段。

后续会经过三天的投票期，必须获得超过4%的投票。一旦收到最低投票门槛，通过的提案将在时间锁中排队。在通过的提案被实施到  Compound 协议中之前，将有 2 天的宽限期。用户可以通过在二级市场上购买 COMP 代币来获得 COMP 代币，或者通过在 Compound  协议上借出或借入 COMP 代币进行收益耕作。 COMP 代币根据 Compound 上借贷活动的利率按比例分配。

这里可以治理些什么呢，比如利率的计算和调整这样。

在compound里钱包里的资产比如DAI放进去会变成cDAI，Ether会变成cEther，假设您在 2020 年 1 月 1 日提供了 1,000 DAI，并且 APY 在整个 2020 年一直保持在 10%。

2020 年 1 月 1 日，在存入 1,000 DAI 后，将获得 1,000 cDAI。在这种情况下，DAI 和 cDAI 之间的汇率为 1:1。  2021 年 1 月 1 日，一年后，您的 1,000 cDAI 现在将增值 10%。 DAI 和 cDAI 之间的新汇率为 1:1.1。您的 1,000  cDAI 现在可以兑换 1,100 DAI。

### Avae

Avae相比Compound更加复杂，主要有8个关键特征：

- 支持更多的不同资产
- 贷款的稳定利率和可变利率：借款人可以灵活地选择稳定利率或可变利率
- 利率转换：借款人还能够在稳定利率和可变利率之间进行转换
- 抵押品互换(Collateral Swap)：借款人可以将其抵押品换成另一种资产。这有助于防止贷款低于最低抵押率并面临清算。
- 用抵押品还款：借款人可以通过在一笔交易中直接用抵押品支付来关闭他们的贷款头寸
- 闪电贷款(Flash loans)：如果借款人在同一笔交易中偿还贷款以及任何额外的利息和闪电贷款费用，借款人可以接受零抵押贷款。闪电贷款对套利交易者很有用，因为它们在跨各种 DeFi Dapp  进行套利交易时具有资本效率。
- 闪电清算(Flash Liquidations)：清算人可以利用闪电贷款借入资金作为清算债券的一部分，并在不使用其资金的情况下获得清算奖金。
- 本地信用授权(Native Credit Delegation)：借款人可以将他们的信用额度扩展到其他希望在没有抵押品的情况下借款以获得更高利率的用户。

Avae中的借贷利率也是由算法决定的，跟供需关系有关。

Avae中存在：

- Stable Annual Percentage Rate(APR)：稳定利率类似于固定利率，但如果市场条件变得糟糕，它可能会随着时间而改变。选择稳定利率的借款人更愿意知道要偿还的确切利息金额，并且不太可能受到各个流动资金池中流动性波动的影响。
- Variable Annual Percentage Rate(APR)：可变利率是根据 Aave 协议中资产的供需情况通过算法确定的。浮动利率的波动与储备中可用的流动性数量相对应。

在Avae里，你获得的是aToken，Compound里面是cToken。Avae也可以在其[网站](https://app.aave.com/)上直接连接Metamask的钱包，非常的方便。

![image-20220416235651244](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416235651244.png)

#### Avae的治理

Aave  于 2020 年 12 月重新启动了其协议的第二次迭代（Aave V2）。其原生治理令牌被称为 AAVE。任何人都可以自由地为 Aave  的改进和调整提出想法。以下是关于如何提出提案的概述。 

1. 在 Aave 治理论坛上准备一份 Aave 征求意见 (ARC) 提案。社区将对此进行反馈。 
2. 如果 ARC 没有争议，可以提交 Aave Improvement Proposal (AIP)。 
3. AIP提交协议去等待投票

