---
timezone: Asia/Shanghai
---


---

# wayhome

1. 自我介绍

互联网老兵一枚，目前对 Defi 比较感兴趣，尤其是 Solana 和 Ton 生态，希望能借此机会了解的更深入一些

2. 你认为你会完成本次残酷学习吗？

我认为会

## Notes

<!-- Content_START -->
### 2024.08.27

- 学习 LXDAO 公开课视频 https://www.youtube.com/watch?v=Is70Ybq28Ls

### 2024.08.26
Solayer

#### 再质押

再质押是由 Eigenlayer 提出的一个概念。这一概念允许质押者使用他们在以太坊上已经质押的资产，作为在其他PoS证明系统（也称为主动验证服务，Actively Validated Services，简称AVS）中的抵押品，来增强其加密经济的安全性

Solayer 是原生构建在 Solana 上的高级重新质押协议，旨在为链上去中心化应用程序（dApps）提供更高的网络带宽，同时增强 L1 安全性。

虽然 Solana Restaking 与以太坊的 Restaking 名字相同，但是两者业务的侧重点和目标客户群完全不同。

**Eigenlayer 更侧重于对外提供服务（外源性 AVS），而 Solayer 更侧重于 Solana 内部应用提供服务（内源性 AVS），当然，Solayer 也可以对外扩展，目前只是 Solayer 的第一阶段。**

#### 核心组件

##### **再质押架构**

Solayer 的再质押组件包括：

- 再质押池管理器：监督资产流动并转换为 Solayer 特定的代币（例如，sSOL）
- 委托管理器：处理跨验证器和 AVS 的权益分配
- 权益池：管理验证器选择和 MEV 增强的回报

##### **共享验证器网络**

- SVN 促进跨链互操作性，使得基于 Solana 的区块链能够共享安全性。
- 优化资源分配：根据权益高效地分配网络资源。

#### 业务模式

**设想 Solana 是一条高速公路，拥有多个车道，不同车道的收费及拥堵程度不同，代表着不同的 Staking Tiers。而不同 DApp 作为通行的汽车所需速度和能接受的收费也有所差异。Solayer 通过接受用户资金委托充当着协调汽车（DApp）、高速公路各个车道（Validators）、各个车道的收费站（Restakers）等多方的角色。**

参与 Solayer Restaking 的用户的收益来自于三个方面：

- Solana Staking Rewards；
- MEV 收入；
- 可能的 Solayer 代币空投；

### 2024.08.25
Solana 

#### 共识机制 POH

PoH 工作流程，从一个随机值开始，运行 hash 函数，并将输出（output）作为输入（input）再次运行该函数。记录函数执行的次数（index）以及每次调用的结果（output)。次数，提供了顺序和时间两个维度的支持；将输出作为输入，依次头尾相连，形成了一条完整的证据链。

由于PoH流是可验证有序的，在进行hash计算时我们会加入额外数据，如：Hash次数，事件信息等。因此，无论数据消息以多快的速度或多少被记录到基于PoH的数据结构中，我们都可以通过输入指定的次数和事件信息等来确定hash(区块)的先后顺序

当生成一个新区块时，我们可以将块的数据和结构进行切片并同时在多核上并行运行验证，当验证完成后将会在Solana网络上进行广播。同时，由于区块的时序性，并且在各个节点中有一致的时间钟，我们很容易验证区块的有效性并且确定区块的先后顺序。

#### 共识机制 POS

**Leader**（出块者）和 **Validator**（验证者）

两者实际上都是质押了 SOL 代币的全节点，只是在不同的出块周期内，Leader 会由不同的全节点来充当，而没有当选 Leader 的全节点会成为 Validator。

选择验证者方面， Solana 采用的是 PoS（权益证明）机制:

- **质押的代币数量**
- **节点的性能**
- **网络延迟**
- **节点的可用性**

#### Solana 共识机制的整体流程

1.**生成交易：** 用户创建并广播交易，包含交易的详细信息和数字签名。

2.**PoH 链上的排序：** 交易的哈希通过数字签名连接到 PoH 链上。由于 PoH 链是有序的，交易也就被排序了。

3.**Validator** **验证：** Validator 负责验证交易的有效性，并选择哪些交易将包含在下一个区块中。Validator 的选择可能基于质押的代币数量、验证者的性能等因素。

4.**交易打包成区块：** Validator 选择的交易被打包成一个区块，其中包括一个特殊的块生产交易，它包含了当前 PoH 链的哈希以及其他信息。

5.**区块传播和确认：** 区块广播到整个网络，其他节点验证并确认区块的有效性。确认后，区块和其中包含的交易就被添加到整个区块链中。

#### 账户

分类：

- 用户账户：普通的钱包用户，类似于以太坊的 EOA 账户。
- 程序账户：执行指定任务的账户，存储了程序的二进制文件
- PDA(Program Derived Addresses)：程序派生地址。该类账户存储程序的状态，即程序执行过程中存储的数据，跟以太坊的状态是一个概念，只不过在这里被拆分到了单独的账户中
- ATA(Associated Token Account)账户：关联账户。它是用户与特定的 SPL（Solana Program Library）Token 代币关联的账户，主要作用是允许用户方便管理他们持有的代币。

租金

用户支付租金以将数据存储在 Solana 区块链上。如果账户无法支付租金，系统将删除这个账户，以减少为那些不再维护的数据花费存储成本。如果账户中的资产超过两年租金的最低余额，那么这个账户可以免交租金 (0.0026 SOL)。

#### PDA

PDA指的是“程序派生地址”（Program Derived Address).这是一种特殊类型的地址，由 Solana 的程序生成，而不是由用户的私钥直接派生。***PDA的主要目的是允许程序拥有和控制某些数据或资产，而不需要传统的私钥签名***。

程序的地址， program_id 是公钥，但这个公钥没有对应的私钥，它不是从私钥派生/衍生出来的。

在区块链中，你需要一个私钥来证明你拥有一个公钥的所有权，同时你才能签字同意这个账户的转账请求。但如果这个账户的所有者不是一个人而是一个去中心化程序，那么把私钥放在这个程序上就不是一个好主意。这时我们就需要一个没有私钥的 PDA。 这样程序不需要私钥就能对一个地址进行签名操作

#### Solana 的程序

分为：

- **On-chain Programs：**这些是部署在 Solana 上的用户编写的程序，由开发者在 Solana 网络上根据具体业务场景开发的程序。
- **Native programs：**这些是集成到 Solana 核心模块中的程序。它们提供了验证节点（validator）运行所需的基本功能。native programs 只能通过网络范围内的软件更新进行升级。
    - [System Program](https://docs.solana.com/developing/runtime-facilities/programs#system-program) 这个程序负责管理建立新账户以及在两个账户之间转账SOL
    - [Solana SPL](https://spl.solana.com/) 程序定义了一系列的链上活动，其中包括针对代币的创建，交换，借贷，以及创建质押池，维护链上域名解析服务等
    - [BPF Loader Program](https://docs.solana.com/developing/runtime-facilities/programs#bpf-loader)
    - [Vote program](https://docs.solana.com/developing/runtime-facilities/programs#vote-program)

程序特点：

**代码和数据的分离**。程序存储在程序账户中，它是无状态的，这意味着它们不会在内部存储任何状态，但它是可执行的executable，会执行相应的逻辑

## 交易和指令

**交易（Transaction）**

交易是一组原子性的操作，代表对区块链状态的一系列更改，包括转账代币、调用程序、更新账户状态等。每个交易都具有唯一的签名，并由一个或多个指令组成。交易费用的支付通常使用 Solana 的原生代币 SOL。

**签名：**每个交易都必须由一个或多个账户的私钥进行签名，以确保交易的身份和完整性。

**指令（Instruction）**

指令是交易中的一条具体指令，包含执行指令所需的具体数据，可以包括执行指令的程序唯一标识 program_id、账户列表、指令参数、配置信息等，用于执行一个特定的操作。

每个交易都包含：

- instructions：一个或多个指令
- blockhash：最新的块哈希值
- signatures：指令对应的发起人的签名

交互的最小单元就是交易中的指令（Instruction）。一个交易可以打包多个指令，指令指定调用哪个程序，要读取或修改哪些账户，以及执行程序需要的额外数据

**交易费用**

执行一个交易需要 **Compute unit， 类似 gas fee.** Solana 中交易手续费用于奖励节点，弥补节点的投入成本，同时也在一定程度上减少了网络中无效的交易

以下的一些操作会产生 **Compute unit**：

- 执行SBF指令
- 在程序之间传递数据
- 调用系统调用
- 记录日志
- 创建程序地址
- 跨程序调用

每笔交易都设定了**最大的CU限制**——”**compute budget**”以确保单笔交易的数据量不会过大从而造成网络的拥堵。超过限制后，指令运行将停止并返回错误，从而导致交易失败

手续费的计算公式为: **CU数量 * CU价格 = 手续费用**

**交易的确认**

一笔交易在根据在solana网络上的确认程度可以分为以下几类主要状态:

- 'processed': 查询已通过连接节点获得1次确认的最新区块
- 'confirmed': 查询已通过集群获得1次确认的最新区块
- 'finalized': 查询已由集群完成的最新区块
### 2024.08.24

Solana 和 ETH 的区别

#### **共识机制**

**Solana**使用的是Proof of History (PoH)与Proof of Stake (PoS)的结合，使得网络能够达到**每秒数千笔**交易处理速度。

- PoH ****是 Solana 独有的创新性机制，用于记录和验证区块的时间戳和顺序。PoH 通过在每个区块中引入时间证明，使得节点能够迅速达成共识，而无需等待整个网络确认
- 而 Solana 的 PoS 机制用于选择验证者。验证者是通过抵押一定数量的代币来参与网络验证的。持有更多代币的验证者有更大的机会被选中生成新的区块和验证交易

因此，PoH 确保区块的时间戳和顺序，PoS 则确保网络的安全性和抗攻击性

#### **交易处理能力**

**Solana**支持对交易的并行处理，通过将交易分成多个子集，并将每个子集分配给不同的验证节点进行处理，从而实现交易的并行处理

***以太坊*** 每笔交易串行执行，一笔交易执行完成再开始下一笔交易，状态依次更新，这也限制了以太坊吞吐量长期维持在每秒15笔～30笔，以牺牲性能换来安全性和一致性。不过以太坊交易处理能力的提升，主要是通过Layer2的Rollup方案来实现的， 但这也会导致 MEV 的问题

#### **交易费用（Gas费）**

**Solana**它的交易费用是根据交易的复杂度和大小动态计算的，这意味着，交易费用会根据交易的执行成本而变化，而不是根据网络上的交易量变化

***以太坊*** 的交易费用因网络拥堵而波动，这是一种纯粹的市场机制，网络中交易拥堵情况下你的交易要想被确认，就需要支付高昂的手续费

#### **智能合约**

**Solana**中一切皆账户，它的智能合约也是账户，但细分为***可执行账户***和***数据账户***，前者存储程序的代码，用来执行特定的逻辑，后者存储状态，即程序运行时的数据。

***以太坊*** 的智能合约本身就包含了合约的逻辑代码，以及状态数据。因此合约部署之后，就不支持直接的升级，只能通过代理的方式间接升级，即重新部署一套合约代码，生成新的合约地址，代理再指向这个新的合约地址。

#### 账户

**Solana**中一切皆账户，它的账户就像一个容器（或者电脑中的文件夹），可以包含程序代码、状态数据以及账户元数据。按照功能可划分为***可执行账户***和***数据账户***，前者为存储程序代码的账户，也称为程序账户。后者包括**普通用户账户**和其他非程序账户，这些账户存储了用户的余额、交易历史和其他相关数据，但它们本身不包含程序代码

***以太坊*** 分为***EOA账户***和***智能合约***，前者是普通用户在以太坊网络中的账户，用于存储以太币（ETH）和进行交易。后者是包含智能合约代码和状态的账户，这些账户由合约创建并部署在以太坊区块链上。


### 2024.08.23

- 学习 LXDAO 公开课视频 https://www.youtube.com/watch?v=_sofdktmD_8

### 2024.08.22
#### Uniswap V4 新特性

- 单例取代工厂

在 Uniswap v3 中，我们为每个流动性池部署一个新合约，这使得创建流动性池和执行多池兑换的成本更高。
在 v4 中，我们将所有流动性池保存在一个「单例」合约中，这将很大程度上节约 Gas，因为代币交易将不再需要在不同合约中持有的流动性池之间转移代币。

- 引入 Hooks

引入 hooks 在流动性池的整个生命周期中的关键点执行指定的操作——例如在交易代币之前或之后，或者在 LP 头寸更改之前或之后。

Uniswap V4 目前支持在 8 个特定的位置进行 hook 回调：

  - beforeInitialize / afterInitialize
  - beforeModifyPosition / afterModifyPosition
  - beforeSwap / afterSwap
  - beforeDonate / afterDonate

- 闪电记账系统

使用 V4 中的闪电记账系统，每个操作（交换 / 部署）只会导致内部余额更新，其中余额以「delta」为单位计价。到交换结束时，它只会在一系列计算之后换出净「delta」余额。

在 V4 中，每一个操作会更新内部的一个净余额（delta），在所有操作结束时会校验该值是否为 0，必须保证该值为 0 才能交易成功。当 Flash accounting 和 Singleton 结合时，可以大大简化多跳交易。

### 2024.08.21

#### 自动化做市商 (AMM)

常数乘积函数是自动化做市商（AMM）为资产对定价的方式。该函数构造了一个双曲线，其中对于某个常数 k，有 x = k/y。

存款人，称为流动性提供者（LPs），是这些流动性池的种子。LPs根据每个AMM的预定代币权重（在Uniswap的案例中--每个代币50%）将其代币存入流动性池。

**集中流动性**

Uniswap V3 引入了集中流动性的概念，旨在打造资本效率更高的市场。集中流动性允许流动性提供者（LPs）设定他们愿意提供流动性的价格区间，从而使资本不再均匀分散于整个恒定价格公式曲线，而是可以聚焦于市场活动更为频繁的较窄价格范围内。此外，集中流动性通过向 LPs 提供更多手续费以及增强市场深度，进一步提升了资本效率

#### **使用AMM的相关风险**

**I.价格滑点（Price Slippage）**

**II.抢跑（Front-running）**

三明治攻击

https://nigdaemon.gitbook.io/~gitbook/image?url=https%3A%2F%2Ftva1.sinaimg.cn%2Flarge%2F008i3skNgy1gsat47jc8cj30x80jcq5u.jpg&width=768&dpr=2&quality=100&sign=36c2b329&sv=1

MEV 是 Maximal (or Maximum) Extractable Value 的缩写。在一个区块内，经济能量通过所有传入交易流入区块链。MEV 提取则是通过重新排序、包含和排除交易，从这些能量中收割以谋取金钱利益的行为。

搜索者通过链上数据和内存池寻找 MEV 机会

- 内存池是所有待处理交易暂存的地方，等待矿工提取并打包进下一个区块。由于该池对公众开放，搜索者会监控它以发现可能带来利润的交易
- 链上数据同样公开，亦可通过分析发现机遇。例如，搜索者可以监控以太坊在去中心化交易所（DEXs）上的价格

**III.无常损失（Impermanent Loss）**

### 2024.08.20

#### 去中心化借贷

DeFi 借贷不仅仅是通过存款赚取些许收益，更关乎实现更高程度的自我主权

DeFi 借贷在多个方面超越了传统金融借贷

- 可信中立性：用户无需前往中心化的第三方机构，即可用其资产进行借贷。智能合约全权处理包括利率、抵押和清算在内的所有事宜。
- 无许可：每个人都能平等获得贷款，任何人都可以成为出借人
- 速度：用户无需再等待贷款审批，这加快了放款流程。只要用户拥有必要的抵押物，即可借款。用户仅需准备资金和网络连接即可借款
- 透明度：由于所有交易、资金、合约及活动均在链上进行，任何人都能看到系统变动及市场状况的变化
- 可用性：应用程序可全天候从任何联网计算机访问，无需考虑银行假日，也无需员工执行交易。
- 税务影响：借贷协议允许用户在不对其抵押品产生应税事件的情况下，获得加密资产的杠杆敞口

![https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8e574287-1db9-4703-a2c0-97eaed9de53f_606x526.png](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8e574287-1db9-4703-a2c0-97eaed9de53f_606x526.png)

#### **APR vs APY**

- **APR（年化利率）**:
    - APR 是不考虑复利的年化利率。它表示一年中借贷的利率，但不包括因利息复投而增加的收益。
    - 公式：APR = (周期利率) × (一年中的周期数)
    
    例如，如果你每月获得 1% 的利率，那么 APR = 1% × 12 = 12%。
    
- **APY（年化收益率）**:
    - APY 则考虑了复利的影响。它表示在一年中，如果利息不断复投，最终的年化收益率是多少。
    - 公式：APY = (1 + 周期利率) ^ (一年中的周期数) - 1

         例如，假设每月的利率仍然是 1%，那么 APY = (1 + 0.01) ^ 12 - 1 ≈ 12.68%。

#### 流动性池

流动性池是由智能合约锁定的代币对或组合，例如 USDC/ETH 或 DAI/USDC/USDT/FEI。这些池为协议上发生的交易提供流动性，并使用户能够兑换进出池内特定的代币

池流动性越深，即池中每种代币数量越多，交易对池内代币相对数量及代币交易时价格变动的影响就越小。换言之，池中代币越多，每次交易产生的滑点就越少。滑点是指从一种代币兑换到另一种代币时，交易中损失的价值量

#### AMM

AMM 通过使用流动性池而非买卖双方市场来实现代币交易，是支撑去中心化交易所的核心技术

AMM 使用户能够自动且无需许可地进行交易，无需中介介入。这正是 AMMs 的真正力量所在：加密货币用户不再受制于中心化交易者和订单簿

AMM 主要有三种类型：Uniswap、Curve 和 Balancer 上的那些。Uniswap 的模式最为常见，允许用户以 50/50 的比例创建任意两种代币的流动性池。Curve 则针对相似资产创建流动性池，而 Balancer 支持最多包含八种不同代币的资产池。

#### 稳定费

稳定费是针对借出资金余额收取的可变年费率。其概念类似于信用卡的可变年利率，例如，若你借入 1,000 DAI，稳定费率为 2.5%，一年后你将欠 Maker 1,025 DAI。若在一年内还清贷款，所欠利息将按比例减少，并计算至还款交易发起的那一刻

#### 抵押率

抵押率表示为贷款所承诺抵押品价值与未偿债务价值之比的百分比

Collateralization Ratio = (Collateral Value/Debt Value) x 100

借贷协议通常会设定最低抵押率以超额抵押债务，即要求提供的抵押品价值远超所借贷款。若抵押率降至该贷款协议规定的最低要求（即清算比率）以下，贷款将被视为抵押不足，并可能被自动清算。

#### 利率模型

利率模型用于确定资产供应者因其贡献而获得的报酬，以及借款者必须为所借资产支付的金额。该模型试图平衡三个变量

- 池流动性
- 借款利率
- 供应速率

DeFi 中常见的利率模型是一种分段函数，呈现出两个不同的斜率。其设计理念在于营造一个资金池既高效利用资本，又具备足够流动性供用户进出池的环境。不同资金池针对不同的利用率目标，但总体而言，利率作为工具旨在维持目标利用率。

![https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F798dc321-0e56-46c3-ae7e-7e9865bda41b_976x436.png](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F798dc321-0e56-46c3-ae7e-7e9865bda41b_976x436.png)

在上面的例子中，该池的目标是达到 90%的利用率，这一点通过 90%处的拐点得以体现。

如果利用率较低（介于 0%至 90%之间），模型将通过低借款利率激励借贷。这些低利率会吸引用户从资金池中借取资产，从而提高利用率

然而，若利用率较高（超过 90%），借款利率会急剧上升，使得借款成本增加。此举激励借款者归还资产，以规避高利率，进而将利用率降至 90%以下。

#### **清算**

当存入的抵押品价值降至抵押率低于最低要求时，借贷平台会自动出售借款人的抵押物以偿还未结债务及可能产生的费用或罚金。债务清偿后剩余的任何抵押品将返还给借款人。

清算价格 = (未偿还债务 x (最低抵押率/100)) / 抵押代币数量

#### 闪电贷

闪电贷允许用户在极短时间内（同一区块内）无需提供抵押物即可借取资产。这类贷款通常用于不同 DeFi 协议间的套利机会。不存在资金损失的风险，因为若贷款未能在同一交易内偿还，该贷款即视为无效。

*一般来说，只要您需要一笔临时贷款且确信能在交易结束时偿还，就可以使用闪电贷*


### 2024.08.19

#### 学习稳定币相关内容

- MakerDAO
  
  MakerDAO 是一个去中心化自治组织，旨在管理以太坊上的 Maker 协议，提供稳定币 DAI 和衍生金融体系。
  RWA 作为 MakerDAO 的重要议题，被视为解决抵押品价值不稳定问题的关键方案，以支持稳定币 DAI 的大规模采用和可持续发展
  对于 MakerDAO  这样的巨型借贷协议来说，**关键的考量因素是：抵押品的价值稳定**


- RWA

  现实世界资产代币化（Real World Asset Tokenization），即将现实世界中的资产通过区块链技术进行代币化表示。现实世界资产存在于链下，所有者可从中获得预期收益，相关权属收益由法律体系规范。
  RWA 最重要的是资产端和资金端，两端都有各自的需求。

  资产端需求：

  * 现实世界资产端的需求是融资，无论是通过 Security Token Offering 的方式，还是通过抵押借贷（如 Centrifuge）的方式。
  * 资产融资的本质是获取资本的来源变为 DeFi 的即时流动性，以及利用区块链和智能合约在融资渠道上实现降本增效。
 
  资金端需求:
  * 加密资本资金端的需求是投资，关键是捕获风险低、稳定生息、可规模化、与加密波动无关的现实世界资产。
  * 从稳定的角度来看，稳定币是关键用例，作为交易媒介，不受加密波动影响；从稳定 + 生息 + 规模化的角度来看，美债 RWA 是关键用例，帮助捕获无风险收益。
  * RWA 能够创造 U 本位的生息资产，成为加密世界的一种新的资产类别，这种资产类别与 DeFi 的可组合性能够带来很大的想象空间，如生息稳定币项目和生息 Layer 2 项目。

- DAI（可简单理解成以太坊上的美元）
  DAI 是 MakerDAO 协议提供的第一个去中心化的基础稳定货币，可简单理解成以太坊上的美元

  DAI 系统运行逻辑：用户通过抵押资产创建 Vault 生成 DAI，涉及存入、借出、偿还和赎回四个操作，未偿还时会涉及利率调整和清算。
  ![DAI 原理](https://img.foresightnews.pro/202303/1261514c11f32db96f7825055e2a2f78.png)
  



<!-- Content_END -->
