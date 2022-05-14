---
title: DeFi Learning Beginner
date: 2022-04-15 15:45:05
tags: Study
categories: DeFi
author: Lcy
---

A reading note for 《How to DeFi Beginner》
# Part One: Centralized & Decentralized Finance

## 第一章 中心化和去中心化金融

从传统的角度看，银行显然是我们最为熟悉的中心化的金融机构。但是啊，这个08年金融危机吧，也可以看出来银行是有一定的风险的，体现了一定的金融系统缺陷。

Defi想要构建什么？

Defi想要用区块链&互联网去重构银行系统中的：

- 支付和清算系统，也就是简单来说汇款
- 可访问性
- 集中化和透明度

### 1. 支付清算系统

如果我们只考虑国内的支付，那，显然没啥意思，但是对于跨境支付的话，这就很麻烦了，不论从时效性还是各种文件balabala都很烦，以及隐私等等都太烦了，这时候Defi来了，加密货币的支付时很快的，同时手续费也会很低。

### 2. 可访问性

这点也是我开始并不理解的，事实上很多人因为信用问题又或者仅仅是某些国家的地理及贫困，到2017年还有17亿人没有储蓄账户，但其中2/3的人可以使用手机，因此DeFi可以为他们提供一个不需要银行储蓄账户的，无国界的无审查但可访问的金融账户。

### 3. 集中化和透明性

传统银行是中心化的，08年雷诺银行倒闭引起金融危机，包括美国也有500家银行倒闭过，这都是巨大的金融风险。另外从我们现在的角度看很多基金、银行是缺乏透明性的，我们不知道我们的资产在哪里。但是DeFi可以解决这个问题，本身是在区块链之上构建的，他就是一行行的代码，是透明的，同时代码对每个人都是公平的，他不会歧视，不会性别歧视、地域歧视、种族歧视、什么都不会。

### 去中心化金融对比传统金融

> The DeFi movement is about bridging these gaps and making finance accessible to  everyone without any form of censorship. In short, DeFi opens up huge windows of  opportunities and allows users to access various financial instruments without  any restriction on race, religion, age, nationality, or geography. When  comparing both traditional and decentralized financial products, there will be  pros and cons on each side. In this book, we will walk you through the concepts  and possibilities of decentralized finance so that you will know how to use its  best features to solve real-world problems.

## 第二章 DeFi是什么

DeFi 即 Decentralized Finance

是一种允许用户在不需要依赖中心化实体的情况下利用借贷和交易等金融服务的运动。这些金融服务是通过去中心化应用程序（Decentralized Applications，Dapps）提供的，其中大部分部署在以太坊平台上。

为了更好的理解一下DeFi的去中心化，将去中心化程度做了三层次的分层，他们的特点如下：

|      | 中心化                                                       | 半中心化                                                     | 去中心化               |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------- |
| 特征 | 托管，使用集中的价格馈送，集中确定的利率，集中提供的追加保证金流动性 | 非托管、去中心化的价格反馈、无需许可的追加保证金通知、无需许可的保证金流动性、去中心化利率确定、去中心化平台开发/更新 | 所有东西都是去中心化的 |
| 例子 | Salt, BlockFi, Nexo and Celsius                              | Compound, MakerDAO, dYdX, and bZx                            | 现在还没有             |

### DeFi的九大类别

#### 1. 稳定货币 Stablecoins

比如USDT是锚定1美元的这种稳定货币

#### 2. 借贷

传统金融系统要求用户拥有银行账户才能使用他们的服务，这是目前  17  亿人所没有的奢侈品。从银行借款还有其他限制，例如具有良好的信用评分和有足够的抵押品以使银行相信其信誉良好且能够偿还贷款。去中心化借贷消除了这一障碍，允许任何人抵押他们的**数字资产**并使用它来获得贷款。人们还可以通过**为贷款池做出贡献**并从这些资产中赚取利息来获得资产收益并参与贷款市场。通过去中心化借贷，不需要银行账户，也不需要检查信用度。

#### 3. 交易所

要将一种加密货币换成另一种，可以使用 Coinbase 或 Binance  等交易所。像这样的交易所是中心化交易所，这意味着它们既是交易资产的中介又是托管人。这些交易所的用户无法完全控制他们的资产，如果交易所被黑客入侵并且无法偿还债务，他们的资产就会面临风险。

去中心化交易所旨在通过允许用户在不放弃对其资产的保管权的情况下交换加密货币来解决这个问题。通过**不在中心化交易所存储任何资金**，用户无需信任交易所就能保持偿付能力。

#### 4. 衍生品

衍生品是一种合约，其价值来自另一种标的资产，例如股票、商品、货币、指数、债券或利率。交易者可以使用衍生品来对冲风险。例如，假设您是一家手套制造商，想要对冲橡胶价格意外上涨的风险。您可以从您的供应商处购买一份期货合约，以便在特定的未来交割日期以今天的约定价格交割特定数量的橡胶。衍生品合约主要在中心化平台上交易。

DeFi 平台同样也要建立去中心化的衍生品市场。（Chapter 8）

#### 5. 基金管理

基金管理是监督资产并管理其现金流以产生投资回报的过程。在 DeFi 中，一些项目已经开始允许以去中心化的方式进行被动资金管理。  DeFi 的透明性使用户可以轻松跟踪其资金的管理方式并了解他们将支付的成本。

#### 6. 彩票

好家伙彩票也算，有意思。这个就不用解释了。

#### 7. 支付

DeFi想要创造一种规模更大，准确性更高的即用即付方式。

#### 8. 保险

去中心化的代币可能受到黑客的攻击所以DeFi也想要提供一种去中心化的保险，毕竟智能合约是不是永远安全的没人知道。代码的安全性度量一直是一个问题，无法量化解决。

#### 9. 治理

治理本质上是加密的业务管理理念。为了让  DeFi 协议管理项目，通常会引入治理令牌以赋予用户投票权并在协议的路线图中拥有发言权。自然，还开发了多个工具包和 Dapps  以促进有效治理和补充现有系统。

# Part Two: Getting into DeFi

## 第三章 去中心化层：以太坊

其实以太坊对于了解区块链的人来说并不陌生，所以这一章看看就简单过去了，感兴趣的去了解一下以太坊基础知识也就足够。

### Dapp的特点：

- 不变性：一旦智能合约在区块链上部署了那必然是不会再变的。==然而这也会导致不可避免的错误被保存下来搞出大问题==
- 防篡改：链上智能合约不可能在大家不知道的情况下被私自篡改
- 透明性：链上智能合约是公开可审计的。==这可能会让黑客审计代码发现漏洞然后攻击，比如THE DAO==
- 可用性：只要以太坊不GG，就一直可用
- 可扩展性：==通常DAPP仅限于所处的链，当然现在跨链非常的火热，另当别论了==

### 代币协议标准

以太坊上流行的代币协议有ERC-20和ERC-721。ERC-20 代币是可替代的，这意味着它们可以互换并且具有相同的价值。另一方面，ERC-721  代币是不可替代的，这意味着它们是唯一且不可互换的。一个简单的类比是将 ERC-20 视为金钱，将 ERC-721 视为可动人偶或棒球卡等收藏品。

现在很火的NFT就是ERC-721协议下的。



## 第四章 以太坊钱包

钱包的本质就是一个公私钥对，主要分为托管钱包和非托管钱包：

- 托管钱包（custodial wallet）：第三方代为保留并保持对加密货币的控制权，比如交易所啊啥的，有被盗风险，比如Mt. Gox就损失了超过85W个Bitcoin
- 非托管钱包（non-custodial wallet）：自己保存自己的公私钥对

我很久前自己创建过ethereum的钱包，不过也确实早已不记得自己的钱包信息了，这篇文章也给了两个比较适合DeFi学习的创建自己钱包的方式。

一个是手机端的[Argent](https://argent.link/coingecko)，作为安卓用户，阿不，鸿蒙用户，似乎有点 GG，欸，先去搞个桌面端的。

桌面端是[Metamask](https://metamask.io)，一个谷歌浏览器的插件，同样也是非托管的钱包。

注册完是这个样子：

![image-20220416102554883](https://luochengyu.oss-cn-beijing.aliyuncs.com/img/image-20220416102554883.png)

助记词一定要记好，不然的话账户可能就找不到了。

然后你能得到你的公钥比如：0xB6EC82B364ade9451D106998a9DB8584d924a306

这个地址欢迎打钱谢谢！

# Part Three: Deep Diving into DeFi

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

## 第九章 去中心化的基金管理

基金管理是监督资产并管理其现金流以产生投资回报的过程。我们已经开始看到创新的  DeFi  团队为用户构建了以去中心化方式更好地管理资金的方法。

去中心化的基金管理是在没有投资经理的情况下进行的。相反，算法可以帮助您自动进行交易。这使您可以选择最适合您的财务目标并减少支付费用的资产管理策略。

### TokenSets

TokenSets 是一个允许加密用户购买启用策略的代币 (SET)  的平台。这些代币具有自动化的资产管理策略，使您能够轻松管理您的加密货币投资组合，而无需手动执行交易策略。使用自动交易策略，您无需手动 24/7  监控市场，从而减少因情绪交易而错失的机会和风险。

#### Index Sets 指数组合

指数集允许用户通过购买单个代币而不是单独购买多个资产来接触更多资产并降低汽油费。最受欢迎的指数集是  DeFiPulse 指数（DPI），该指数基于市值加权指数跟踪 DeFi 代币的表现

#### Yield Farming Set 

Yield  Farming Sets 使用户无需不断地进行多个智能合约交易来产生收益农业协议，从而节省燃料。这些 Sets 的策略将定期索取流动性提供者 (LP)  奖励，将其出售以换取策划资产，并质押这些资产以产生更多的LP奖励。本质上，这是 DeFi 采取复利的一个例子！

可以去[TokenSets – Asset Management Simplified](https://www.tokensets.com/)了解情况。

## 第十章 去中心化的彩票

2020 年 2 月，一位仅存入 10 美元的用户在 PoolTogether 的每周 DAI 奖池中赢得了 1,648 美元，获胜机会为 69,738  分之一。 PoolTogether 彩票最好的部分是，如果参与者没有中奖，他们可以获得 10 美元押金的退款。这场博弈没有输家，只有机会成本。

？？？？有这种好事？

### Pool Together

PoolTogether  是一个去中心化的无损彩票或去中心化的奖金储蓄应用程序，用户可以在抽奖后保留他们的初始存款金额。不是使用购买的彩票来资助奖金，而是使用汇集的用户存款在  Compound 协议上赚取的利息来资助奖金。对于每一轮 PoolTogether，所有用户存款都会发送到 Compound  以赚取利息。每个间隔结束时将随机抽取一名幸运获胜者，以赢取累积的全部利息作为奖金

https://pooltogether.com/zh

可以去上面网站上看看，我没找到支持的货币列表。但是DAI, USDC, UNI,  COMP是肯定可以支持的。

## 第十一章 去中心化支付

### Sabiler 

Sablier  是一个支付流应用程序——这意味着它允许在不同方之间以小增量（以秒为单位！）实时进行支付和取款。考虑在工作和进展过程中实时支付的每小时咨询工作、每日合同工或每月租金支付。与在  Spotify 上流式传输音乐的方式类似，也可以在 Sablier 上流式传输资金！

**什么是流式付款？**

付款人现在可以在双方定义和同意的期限内实时发送付款，而不是等待固定期限（例如，每月、每两周）付款。通过  Sablier，收款人现在可以实时收到他们的付款并随时提取。比如60/h的咨询服务可以在Sablier签订协议后一分钟一分钟的自己付款，即使返回了损失也非常小。

官网：[Sablier](https://sablier.finance/)

等于是形成了一个支付流，一步步付款。

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

## 第十三章 治理

与中心化传统公司不同，DeFi  协议不需要遵循除链上编码之外的任何规则。这通常被称为“代码就是法律”。

### Aragon

[Aragon](https://client.aragon.org/#/)是一个社区驱动的项目，其使命是通过为去中心化组织的繁荣创造工具来赋予自由。随着技术以前所未有的速度发展，人们担心它在创建全球集中控制、监视和压迫制度中的作用。  Aragon 决心创建一个自由、开放、公平的社会。

Aragon Court 是 Aragon  创建的解决方案，它模仿了传统商业世界中法院的功能。当发生冲突时，参与者可以将其升级到Aragon Court，由陪审员决定是否应惩罚任何一方。

陪审员从陪审员池中随机选择，通过锁定  ANJ  代币来审查和裁决争议。与传统法院不同，陪审员在投票支持多数结果时会获得争议费用补偿。因此，该系统不适合不偏不倚的决策，而是依靠社会共识。投票支持少数派结果的陪审员将被带走一部分  ANJ  代币，并奖励给投票支持多数派的陪审员。如果结果不令人满意，任何一方都可以支付费用对争议提出上诉，并由大量陪审员进行审查。这个过程可以重复，直到整个陪审员池对争议做出裁决。

### Snapshot

由于以太坊汽油费上涨，链上投票的成本变得难以承受，阻碍了小代币持有者参与治理过程。 Snapshot试图通过在链下拍摄投票快照来解决这个问题，从而有效地使投票过程无气体。Snapshot 已经看到许多 DeFi 项目利用其工具来建立治理流程。截至 2021  年 1 月，Snapshot 可免费使用，已有多达 418 个不同的项目注册使用 Snapshot。

缺点：链下投票不受智能合约约束。

https://snapshot.page/#/

## 第十四章 DeFi仪表盘

[Zapper - Your Home to Web3](https://zapper.fi/zh)

仪表板是一个简单的平台，可将您的所有 DeFi 活动聚合在一个地方。这是一个有用的工具，可以可视化和跟踪您的资产在不同 DeFi  协议中的位置。仪表板能够将您的资产分为不同的类别，例如存款、债务和投资。

# Part Four： DeFi in Action

## 第十五章 DeFi in Action

### 案例一 Surviving Argentina’s High Inflation

就是阿根廷的货币贬值太猛，但是DAI是和美元挂钩的， 即使DeFi有风险，但是相比阿根廷货币的风险来说不值一提，所以有人用DAI来规避自己资金的风险。（不能直接换美元因为政府不允许。）

[Mariano Conti · Living on Defi: How I Survive Argentina's 50% Inflation · SlidesLive](https://slideslive.com/38920018/living-on-defi-how-i-survive-argentinas-50-inflation)

### 案例二 Uniswap Ban

就是有一段时间Uniswap团队为了遵守美国法律然后ban掉了一些地方的ip。但是实际上只能禁止网站访问不能禁止Uniswap协议，因此呢他就重新建了一些站点用于被banIP的地方的人访问。

## 第十六章 DeFi就是未来！！！

DeFi：

- 透明！
- 可接入！
- 高效！
- 便捷！

DeFi目前的痛点：

- **Wallet** - [Argent](https://www.argent.xyz/) is creating a radically better user-focused crypto wallet  experience, with state-of-the-art security, native integration with DeFi Dapps  such as Compound and others, as well as not needing seed keys. 
- **Participation of  products** - [Zapper](https://zapper.fi/) abstracts away many of the complexities and steps involved  with DeFi products. It also allows users to access multiple financial products  in one transaction, saving time and effort. 
- **User-friendly development** - [Gelato  Finance]([play.gelato.finance](https://play.gelato.finance/)) recently launched their“If this, then that” for crypto. It allows users  to set actions that will be done once certain conditions are met, such as“Buy  ETH when it is $200” or“Send some money to Alice when it’s her birthday.”  
- **Insurance** - Financial market effectively facilitates the transfer of risk - one  man’s hedge against his position is another man’s profit. Insurance is now  available via DeFi insurers such as [Nexus Mutual](https://nexusmutual.io/). If you are willing to accept a  lower yield on the money you have placed on lending protocols such as Compound  in exchange for peace of mind, it can now be done. 
- **Aggregation of liquidity** -  There are many different decentralized exchanges (DEXs) in the market with  varying liquidity. It is a headache for users to choose which one is the best  for their trade. This is slowly becoming a thing of the past with liquidity  aggregators such as [1inch.exchange](https://app.1inch.io/#/), Paraswap, and Matcha helping users to automatically split orders across DEXs to  ensure the best possible execution prices.
- **Yield optimization** - Remember switching around different banks for the best  rates for fixed deposits? You don’t have to do that in DeFi - yield aggregators  such as Yearn.finance, idle.finance, and DeFiSaver automatically allocate your  cryptoassets to places with the best yield opportunities.

# 浅浅小结一下

How to DeFi: Begginer 这本书其实让我认识到了炒币这种事情属于是太low了，DeFi所展望的远远不是简单的炒币，而是真的带来了一种全新的去中心化的金融模式。

完善的借贷、基金、彩票、衍生品等等DeFi合约属于是让人对目前加密货币的发展有了全新的认识。
