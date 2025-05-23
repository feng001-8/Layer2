## ETH2.0

* POW -> POS -> 信标链 -> 共识层
* EIP4844 -> DA链上 -> 分片链结构



### POW 到POS

* POS质押过程改变

> 在信标链合约达成共识，最低32ETH，这也催生出LSD项目 （MAntle的LSD链下的DA服务多一点，Lido 链上服务多一点）

* 区块验证过程





### Epoch Slot Block

* Epoch 具有 32 个slot
* solt 可以有block 也可以没有block

> Epoch是一个周期，32个slot是一个周期，也就是质押周期，验证人验证节点，每经过一个epoch状态变为safe，2个epoch变成finalized不可逆



### EIP4844 分片链

结构：

* 信标链

* 执行层

* 分片层

> 数据周期 ：过21天就清除数据
>
> 费用：用EIP1559去减少gas费用
>
> EIP4844根链下的DA用的技术没有什么区别（ZKG，BLS，纠删码）



### 交易类别

| **类型**             | **EIP**  | **用途**          | **数据结构特点**                | **Gas优化**          |
| :------------------- | :------- | :---------------- | :------------------------------ | :------------------- |
| Legacy Transaction   | -        | 基础转账/合约调用 | 含`gasPrice`                    | 无                   |
| EIP-1559 Transaction | EIP-1559 | 动态Gas定价       | 含`maxFeePerGas`和`priorityFee` | 基础费销毁，减少拥堵 |
| Blob Transaction     | EIP-4844 | Layer2数据存储    | 含`blobVersionedHashes`         | 降低Rollup成本       |