## eigenlayer 

EigenLayer 是以太坊生态中的再质押协议，旨在通过 共享以太坊主网的安全性，允许用户将已质押的 ETH 或流动性质押代币（如 stETH、rETH 等）重复质押到其他区块链应用（如预言机、跨链桥、数据可用性层等），以获取额外收益。其核心理念是 “复用安全性”，降低新项目构建信任网络的成本

## 再质押的流程
* eigenpod的合约支持eth就像LSD玩法
* TOKEN 
-- operator 运营商
-- staker 个人
> 调用合约 registeroprator 注册运营商 接受slash的方法 用于接受shares股份
> 合约 depositinto 到 strategy 质押策略 调用delegate 把shares 给operator  （再质押）
> quenwithdraw  退出(7天) 后面才 comletewithdraw 取钱（退出）

详细逻辑请看eigenlayer项目里面