## Froud froof 和 Zk proof

### 欺诈证明和有效性证明是什么

欺诈证明和有效性证明是用于确保 第二层区块链 rollups 中交易的正确性和安全性的机制，这些是 第一层的扩展方案。这些证明使得 rollups 能够通过离线处理交易，同时利用以太坊的安全性，来实现更高的吞吐量和更低的 gas 成本。

### Froud froof （欺诈证明）

欺诈证明是一种机制，允许任何人挑战并证明某个交易或状态转换是无效的。

1. **交易提交**：用户提交交易到区块链网络。
2. **状态转换**：网络处理交易并更新状态。
3. **挑战期**：在挑战期内，任何人都可以质疑交易的有效性。
4. **欺诈证明**：如果发现无效交易，提交欺诈证明，撤销该交易。

###  Zk proof （零知识证明）ZKP

零知识证明是一种密码学技术，允许一方（证明者）向另一方（验证者）证明某个陈述是真实的，而不透露任何关于该陈述的额外信息。就像你向朋友证明你知道一个秘密，但不需要告诉他秘密是什么。

1. **陈述**：证明者声称某个陈述是真实的。
2. **证明**：证明者生成一个零知识证明，证明该陈述的真实性。
3. **验证**：验证者验证零知识证明，确认陈述的真实性，而不需要知道任何关于陈述的细节。

> 两种开发 后端算法开发 （zk-SNARKs（零知识简洁非交互式知识论证），zk-STARKs（零知识透明可扩展知识论证）和前端开发（电路约束 **Circuit Constraints**）
>
> 库：
>
> https://github.com/risc0/risc0。
>
> https://github.com/arkworks-rs/snark
>
> 

### 欺诈证明的优缺点

**优点**：

- **高吞吐量**：默认交易有效，无需每笔交易都验证。
- **低费用**：通过批量处理，大幅降低交易成本。

**缺点**：

- **挑战期**：需要等待挑战期结束，交易才能最终确认。
- **复杂性**：实现欺诈证明机制需要复杂的智能合约和数据结构。

### 零知识证明的优缺点

**优点**：

- **隐私保护**：不透露任何关于陈述的额外信息。
- **即时确认**：交易一旦提交，立即得到确认，无需等待挑战期。

**缺点**：

- **计算复杂度**：生成和验证零知识证明需要大量的计算资源。
- **实现难度**：实现零知识证明机制需要复杂的密码学算法。

> 圆锥曲线方程 有限域等等 考研西电的时候密码学原理如何解有限域的圆锥曲线方程的解



## 欺诈证明与零知识证明的对比

| **特性**         | **有效性证明（ZK-Rollup）**       | **欺诈证明（Optimistic Rollup）**  |
| :--------------- | :-------------------------------- | :--------------------------------- |
| **信任模型**     | 无需信任，数学保证正确性          | 依赖至少一个诚实节点挑战欺诈       |
| **最终性时间**   | 即时（分钟级）                    | 延迟（7 天挑战期）                 |
| **L1 Gas 消耗**  | 每次提交需支付验证证明的 Gas      | 仅争议时支付 Gas，正常情况成本更低 |
| **计算资源需求** | 高（生成证明需要专用硬件）        | 低（仅争议时需计算）               |
| **适用场景**     | 高频交易、即时结算（如支付、DEX） | 通用型应用，对延迟不敏感的场景     |

比特币详细参考：https://www.panewslab.com/4/articledetails/17bokh5i.html （BitVM背景知识：欺诈证明与ZK Fraud Proof的实现思路）

> tip： bitget是用moph链 用的是上面两种的结合

**代码实现：**

```solidity
// 简化版 ZK 验证合约逻辑（以 zk-SNARKs 为例）
contract Verifier {
    function verifyProof(
        bytes32[2] memory a,
        bytes32[2][2] memory b,
        bytes32[2] memory c,
        bytes32[] memory inputs
    ) public view returns (bool) {
        // 调用预编译的椭圆曲线验证合约
        return snarkverify(a, b, c, inputs);
    }
}
```

```solidity
// 简化版欺诈证明验证逻辑
contract OptimisticVerifier {
    function challengeBatch(
        bytes32 batchHash,
        uint256 disputedStep,
        bytes calldata proof
    ) public {
        // 1. 加载争议批次的状态根
        bytes32 expectedState = getStateRoot(batchHash);
        // 2. 根据欺诈证明重现计算步骤
        bytes32 computedState = executeStep(disputedStep, proof);
        // 3. 验证结果是否一致
        require(computedState != expectedState, "挑战失败");
        // 4. 触发回滚并惩罚作恶者
        slashOperator(batchHash);
    }
}
```