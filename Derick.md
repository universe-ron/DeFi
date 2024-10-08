# Derick

1. 自我介绍: 
2. 你认为你会完成本次残酷学习吗？  **100%**


## Notes

<!-- Content_START -->

### 2024.08.14
- 今天参加了Marcus和q老师的开营启动课，对DeFi有了初步了解
- [第一节课笔记](https://blog.ithuo.net/posts/defi-1-decentralized-finance/)

### 2024.08.19
- 学习这篇[去中心化指数](https://nigdaemon.gitbook.io/how-to-defi-advanced-zhogn-wen-b/di-9-zhang-qu-zhong-xin-hua-zhi-shu)
- 去中心化指数和传统ETF虽然都是追踪某个资产组合的投资工具,但它们之间存在一些重要区别:
1. 发行和管理方式:
   - 传统ETF由中心化的金融机构发行和管理。
   - 去中心化指数由智能合约管理,没有中心化的管理机构。

2. 交易场所:
   - 传统ETF在证券交易所交易。
   - 去中心化指数在去中心化交易所(DEX)交易。

3. 资产托管:
   - 传统ETF的资产由托管机构保管。
   - 去中心化指数的资产直接存储在区块链上的智能合约中。

4. 赎回机制:
   - 传统ETF通常只允许授权参与者进行大额赎回。
   - 去中心化指数允许任何持有者随时赎回基础资产。

5. 监管:
   - 传统ETF受到严格的金融监管。
   - 去中心化指数目前监管较少,处于灰色地带。
### 2024.08.20
- 根据提供的信息，我将总结USDT、USDC和DAI这三种稳定币的产生方式以及限制超发的机制:

## USDT (Tether)
### 产生方式
USDT是由Tether公司发行的中心化稳定币。
### 限制超发机制
- Tether声称每个USDT都由等值的美元储备支持，以实现1:1的价值关系。
- 用户可以通过Chaineye工具查看Tether的资产负债情况和储备金分布。
- 然而，Tether的储备并非完全透明，存在被公司挪用的风险。
## USDC (USD Coin)
### 产生方式
USDC由Centre组织(Coinbase和Circle共同创建)发行的中心化稳定币。
### 限制超发机制
- Circle声称每个USDC都有相应的美元作抵押，存放在需要定期审计和公开报告的账户中。
- USDC的储备金接受审计，提高了透明度。
- 用户可以通过Chaineye工具查看Circle的资产负债情况和储备金分布。
## DAI
### 产生方式
DAI是由MakerDAO发行的去中心化、超额抵押稳定币。
### 限制超发机制
- 用户通过将加密资产(如ETH)作为抵押品锁定在智能合约中来铸造DAI。
- 系统要求维持较高的质押率，以抵御市场波动风险。
- DAI的铸造和销毁过程由智能合约执行，没有中心化托管风险。
- 目前由USDC抵押生成的DAI已超过总量的60%，引发了对其去中心化程度的质疑。
USDT和USDC作为中心化稳定币，主要依赖发行机构的信誉和监管来限制超发。而DAI作为去中心化稳定币，通过智能合约和超额抵押机制来维持稳定性和限制超发。每种稳定币都有其优缺点，用户需要权衡考虑其稳定性、透明度和去中心化程度。


### 2024.08.21
DEX聚合器是去中心化金融(DeFi)生态系统中的重要组成部分,主要用于优化去中心化交易所(DEX)的交易体验。以下是DEX聚合器的主要特点和功能:
## 主要功能
1. **流动性聚合**: 汇集多个DEX的流动性,解决单个DEX流动性不足的问题。
2. **最优路径**: 使用复杂算法寻找最佳交易路径,优化交换率和燃气费用。
3. **订单拆分**: 将大额订单拆分到多个DEX执行,减少价格滑点。
4. **价格比较**: 实时比较不同DEX的报价,帮助用户获得最佳价格。
## 优势
1. **降低交易成本**: 通过优化路径和拆分订单,减少燃气费用和价格影响。
2. **提高效率**: 用户无需手动在多个DEX间比价和交易。
3. **增强流动性**: 整合分散的流动性,提高整体市场效率。
## 代表项目
一些知名的DEX聚合器包括:
- 1inch
- DODO 
- Matcha
- Paraswap
- KyberSwap
- 0x API

### 2024.08.22
了解去中心化借贷的概念
去中心化借贷是去中心化金融(DeFi)生态系统中的一个重要组成部分。以下是对去中心化借贷的主要特点和运作方式的解释:

## 基本概念
去中心化借贷是指在区块链上通过智能合约实现的点对点借贷服务,无需传统金融机构作为中介。
## 主要特点
1. **无需中介**: 借贷双方直接在区块链上进行交互,无需银行等中间机构参与。
2. **智能合约驱动**: 借贷条款和执行过程由智能合约自动管理。
3. **抵押机制**: 借款人通常需要提供加密资产作为抵押品。
4. **流动性池**: 多个贷方的资金汇集在流动性池中,供借款人借贷。
5. **利率市场化**: 利率根据供需关系自动调整。

## 运作流程
1. 贷方将加密资产存入借贷协议的流动性池。
2. 借款人提供抵押品并从流动性池中借出资产。
3. 智能合约自动管理借贷条款,包括利率计算、抵押品监控等。
4. 借款人可随时偿还借款,贷方可随时提取存款及利息。
## 优势
1. **可访问性**: 为全球用户提供金融服务,特别是没有银行账户的人群。
2. **透明度**: 所有交易都记录在区块链上,可公开审计。
3. **效率**: 自动化执行降低了运营成本,提高了效率。
4. **灵活性**: 用户可以灵活地存取资金,调整借贷头寸。
总的来说,去中心化借贷通过区块链技术和智能合约,实现了一个无需信任、高效透明的借贷市场,为传统金融体系带来了创新和挑战。
### 2024.08.23
学习混合器的概念
## 区块链中的混合器：保护隐私的双刃剑

**什么是混合器？**

在区块链的世界中，混合器（Tumbler或Mixer）是一种服务，旨在通过将多个交易合并在一起，来混淆加密货币的来源和去向，从而增强交易的隐私性。想象一下，你把自己的硬币和其他人的硬币放在一个大袋子里，然后重新分配，这样就很难追踪你的硬币最初来自哪里。

**混合器的工作原理**

1. **存款：** 用户将要混淆的加密货币发送到混合器的地址。
2. **混合：** 混合器将收到的所有加密货币混合在一起，形成一个大的交易池。
3. **分配：** 混合器将交易池中的加密货币重新分配给各个用户，确保每个用户收到的加密货币与最初存入的金额相同，但来源已经变得难以追踪。

**混合器的优势**

* **增强隐私：** 混合器可以有效地保护用户的隐私，防止他人追踪资金的流动。
* **提高安全性：** 通过隐藏交易的来源，混合器可以降低被黑客攻击的风险。

**混合器的争议**

* **洗钱工具：** 混合器也被犯罪分子利用来洗钱，掩盖非法活动的资金来源。
* **监管难题：** 由于混合器的匿名性，监管机构很难追踪非法活动，给执法带来了挑战。

**常见的混合器类型**

* **中心化混合器：** 由第三方机构运营，用户需要信任该机构。
* **去中心化混合器：** 基于智能合约运行，无需第三方机构，安全性更高。

**使用混合器的注意事项**

* **法律风险：** 在一些国家和地区，使用混合器是违法的。
* **安全风险：** 选择混合器时，务必选择信誉良好的平台，以避免资金损失。
* **隐私与透明度：** 虽然混合器可以保护隐私，但过度依赖混合器也可能导致监管不力。

**有哪些应用**
* CoinJoin
* Wasabi Wallet
* Tornado Cash


### 2024.08.24
学习uniswap v3 白皮书 第一章
Uniswap v3引入了几个重要的新特性
## 集中流动性
集中流动性是Uniswap v3最重要的创新之一。它允许流动性提供者(LP)将其流动性集中在特定的价格范围内，而不是像之前版本那样均匀分布在整个价格范围内。
- LP可以选择任意价格范围来提供流动性，这被称为"位置"。
- 每个位置只需要维持足够的储备来支持其价格范围内的交易。
- 当价格超出位置的范围时，该位置的流动性变为非活跃状态，不再赚取费用。
- 这大大提高了资本效率，因为LP可以将资金集中在他们预期价格波动的范围内。
## 灵活费用
Uniswap v3不再固定0.30%的交易费率，而是引入了多个费率选项:
- 初始支持的费率包括0.05%、0.30%和1%。
- 每个交易对可以有多个不同费率的资金池。
- UNI代币持有者可以通过治理添加新的费率选项。
这种灵活性允许市场为不同的交易对选择最合适的费率，提高整体效率。
## 改进的价格预言机
Uniswap v3对其时间加权平均价格(TWAP)预言机进行了重大升级:
- 用户不再需要在链外跟踪累加器的先前值。
- 合约内部存储了累加器的检查点，允许外部合约计算最近期间的链上TWAP，无需存储累加器值的检查点。
- 从算术平均TWAP切换到几何平均TWAP，理论上更准确地表示平均价格。
## 流动性预言机
Uniswap v3引入了一个新的流动性累加器:
- 跟踪每秒钟1/L的累积值，其中L是当前范围内的虚拟流动性。
- 这对外部合约实现流动性挖矿非常有用。
- 还可以用于判断哪个资金池的TWAP最可靠。
## 非同质化流动性
与之前版本不同，Uniswap v3中的流动性位置是非同质化的:
- 费用不再自动复投为流动性，而是单独存储。
- 移除了原生流动性代币，为更灵活的外部包装提供了可能性。

### 2024.08.25
### 2024.08.26
- 在测试网创建V3 POOL,存款1eth，交易[hash](https://explorer-holesky.morphl2.io/tx/0x6a6a419876785cca553859d1648b70c0d3004deaab9a037e169a57bf21e25678)
### 2024.08.27
### 2024.08.28
### 2024.08.29
### 2024.08.30
### 2024.08.31
### 2024.09.01
### 2024.09.02
### 2024.09.03
### 2024.09.04
### 2024.09.05
### 2024.09.06
### 2024.09.07
### 2024.09.08
### 2024.09.09
### 2024.09.10
<!-- Content_END -->
