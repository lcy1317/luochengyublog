---
title: DeFi Learning(五)
date: 2022-04-16 10:29:03
tags: Study
categories: DeFi
author: Lcy 
---

# Part Three: Deep Diving into DeFi

A reading note for 《How to DeFi Beginner》

## 第五章 去中心化的稳定货币

截止22.4.16有81个稳定的货币，市值前五的有：

![image-20220416143324880](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416143324880.png)

想要看的话可以去[Top Stablecoins by Market Capitalization - CoinGecko](https://www.coingecko.com/en/categories/stablecoins)这个网站去自行查询一下。

### USDT

USDT是与美刀挂钩的，每一美元可以换取1USDT，当然Tether储备金是保存在金融机构中的，我们作为用户想要用的话就需要信任Tether。

### DAI

> Dai 由 MakerDAO 开发并管理，是第一个去中心化基础稳定货币。Dai 由数字资产足额抵押担保发行，和美元保持1:1锚定，1 Dai = 1 美元。

DAI也同样是和一美元挂钩，但是他和USDT不一样的地方在于它可以使用ETH进行抵押。

### Maker 

Maker 是一个运行在以太坊区块链上的智能合约平台，拥有两个代币：DAI（在算法上都与 1 美元挂钩）和它的治理代币——Maker（MKR）。

三个需要知道的关键参数：

#### 1. Collateral Ratio 抵押比率

可以铸造的 DAI 数量取决于抵押品比率。

比如：

- Wrapped Bitcoin (wBTC) collateral ratio = 150%
- Basic Attention Token (BAT) collateral ratio = 150%

因此，150%  的抵押比率意味着要铸造 100 美元，您需要存入至少价值 150 美元的 wBTC 或 BAT。

#### 2. 稳定费

截至 2021 年 4 月，BAT 目前的稳定费为 6.0%。（可以理解为管理费，或者说借贷的利息）

#### 3. DAI Saving Rate (DSR)

DAI  储蓄率 (DSR) 是随着时间的推移持有 DAI 所赚取的利息。它还充当影响 DAI 需求的货币工具。截至 2021 年 4 月，DSR 利率设定为  0.01%。

### 为什么我们要质押ETH换DAI而不是直接换美元呢？

有三种可能的情况：  

-  您现在需要现金，并且您拥有一项您认为将来会更值钱的资产。  在这种情况下，您可以将您的资产保存在 Maker 保险库中，并通过发行 DAI  立即获得资金。
- 您现在需要现金，但不想在出售资产时冒险触发应税事件。 相反，您将通过发行 DAI 来提取贷款。
- 投资杠杆，如果您认为您的资产价值会上升，您可以对您的资产进行投资杠杆。

### 如何获得DAI

![image-20220416191157684](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416191157684.png)

实际上就是在智能合约中质押ETH来铸造DAI。

在[Oasis.app](https://oasis.app)这个网站上可以去铸造属于自己的DAI，他是可以直接关联Metamask的钱包的。

![image-20220416191812985](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416191812985.png)

可以看到这里的质押率以及费率。还挺高的，草。
