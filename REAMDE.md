# 主题

## Layer2 的基本概念和主流项目分析
包含：
> DA（data avaliablity）
> Sequencer
> Rollup service
> verfiyer
> tip: 包含比特币layer2 stacks和sidechains
## ethereum layer2
包含分析项目和代码：
> Arbitrum (op rollup)
Arbitrum rollup fixes this! The basic idea is this: an Arbitrum Rollup Chain runs as a sort of sub-module within Ethereum. Unlike regular, layer 1 ( “L1”) Ethereum transactions, we don’t require Ethereum nodes to process every Arbitrum transaction; rather, Ethereum adopts an “innocent until proven guilty" attitude to Arbitrum. Layer 1 initially “optimistically assumes” activity on Arbitrum is following the proper rules. If a violation occurs (i.e., somebody claims “now I have all of your money”), this claim can be disputed back on L1; fraud will be proven, the invalid claim disregarded, and the malicious party will be financially penalized.
Arbitrum Rollup 解决了这个问题！其基本思路是： Arbitrum Rollup 链作为以太坊中的一种子模块运行。与常规的以太坊 Layer 1（“L1”）交易不同，我们不要求以太坊节点处理每一笔 Arbitrum 交易；相反，以太坊对 Arbitrum 采取 “无罪推定”的态度。Layer 1 最初“乐观地认为”Arbitrum 上的活动遵循正确的规则。如果发生违规行为（例如，有人声称“现在我拥有了你所有的钱”），则可以在 Layer 1 上对此声明进行异议；欺诈行为将被证明，无效声明将被忽略，并且恶意方将受到经济处罚 
https://docs.arbitrum.io/welcome/arbitrum-gentle-introduction
1. 架构分析
2. 充值提现
3. rollup的流程
> Optimism (op rollup)
OP Mainnet is a "Layer 2" system and is fundamentally connected to Ethereum. However, OP Mainnet is also a distinct blockchain with its own blocks and transactions. App developers commonly need to move data and tokens between OP Mainnet and Ethereum. This process of moving data and tokens between the two networks is called "bridging".
OP 主网是一个“第二层”系统，从根本上与以太坊相连。然而，OP 主网也是一个独立的区块链，拥有自己的区块和交易。应用程序开发者通常需要在 OP 主网和以太坊之间转移数据和代币。这种在两个网络之间转移数据和代币的过程称为“桥接”。
https://docs.optimism.io/app-developers/bridging/basics
> PolygonzkeVM （zkevm）
Polygon zkEVM is to Ethereum a Layer 2 network and a scalability solution utilizing zero-knowledge technology to provide validation and fast finality of off-chain transactions.
Polygon zkEVM 是以太坊的第 2 层网络和可扩展性解决方案，利用零知识技术提供链下交易的验证和快速终结。
https://docs.polygon.technology/zkEVM/overview/
> scroll （简单）
> zksyncera （简单）
> scarnet （略）
1. op stack 项目分析
2. 跨链调用 （从L1到L2的充值和L2到L1的提现）
3. rollupde1细节流程 op stack怎么去实现rollup的DA celestia elgenDA EIP4844
4. rollup改造的celestia的细节流程
5. op stack的模块间交流的rpc
6. op stack的区块推到流程 ETH20
7. 基于op stack的开发自己的layer2

1. DA项目 （EigenDA EIP4844 celestia）
> Kate Commitments kate承诺
> Data Availability Sampling （DAS）
2. eigenlayer质押模型
3. eigenDA架构和代码流程
4. EIP4844
5. celestia特性
## 实现 op stack的sdk 从L1到L2的充值和L2到L1的提现