---
timezone: Europe/Berlin
---
1. 自我介绍
   我是一名传统行业的系统toB产品经理
2. 你认为你会完成本次残酷学习吗？
   我最近工作有一点忙，不确定是不是能够每天都能坚持，但是至少周末可以

## Notes

<!-- Content_START -->

### 2025.02.06

# 历史
"Crypto Anarchist Manifesto" Tim
Tim 1998年发布加密无政府宣言，将匿名数字交易视为个人自由的基石

90年代cryptopunks曾多次尝试创建数字货币

David Chaum 推出了DigiCash，首次展现了匿名数字经济的雏形。然而，它依赖于现有的金融基础设施，并且在很大程度上是中心化的。最终，DigiCash 于 1998 年申请破产。

E-gold 于 1996 年晚些时候出现，以实物黄金储备为后盾。在巅峰时期，E-gold 拥有350 万个注册账户，每年促成数十亿美元的交易。然而，2009 年，由于法律问题，转账被暂停。

2008 年，匿名作者中本聪(Satoshi Nakamoto)在一篇题为《比特币：一种点对点电子现金系统》的论文中提出了一种解决方案，解决了如何在没有领导者的情况下达成共识这一悬而未决的问题。比特币确立了一种分布式账本系统，其中的数据以加密方式按时间顺序链接在一起。它还成为第一个去中心化的数字货币，无需底层抵押品即可运行，并且无需银行等受信任的第三方中介机构。


2012 年，Vitalik Buterin和 Mihai Alisie 创办了比特币杂志，这是第一本专注于数字货币的严肃出版物。Vitalik 很快发现了比特币的局限性，并提出了一个支持通用金融应用的平台。

2014年，在Gavin Wood的帮助下，以太坊的设计得以正式化。

2015 年 7 月 30 日，以太坊作为一个平台上线，旨在利用数字货币构建自主经济的工具。

# 协议架构
由两个主要部分组成：
执行层 EL The execution layer
处理实际交易和用户交互

共识层 CL The consensus layer 
提供权益证明共识机制 确保所有节点遵循相同的提示并驱动执行层的规范链


### 2025.02.07
Execution Layer Specification

状态转换函数 state transition function STF
解决两个主要问题: 1)是否可以将区块附加到区块链末尾 2)状态怎样变化

系统的状态并不是储存在某一个特定的位置，系统的状态不是存储在特定位置，而是通过应用状态折叠函数来动态推导。

转换函数步骤：
1. 获取父区块头（Retrieve the Parent Header）
目的：确保新区块基于最新的链状态构建。

操作：从区块链中获取最近一个区块（父区块）的头部信息，包含关键字段如 state_root（状态根哈希）、gas_used（已用 Gas）、timestamp（时间戳）等。

意义：新区块的所有状态转换需基于父区块的最终状态。

2. 验证 Excess Blob Gas（EIP-4844 相关）
背景：EIP-4844 引入携带 Blob 的交易类型（Proto-Danksharding），excess_blob_gas 用于动态调整 Blob 交易费用。

操作：

根据父区块头计算预期的 excess_blob_gas。

检查当前区块头中的 excess_blob_gas 字段是否与计算结果一致。

意义：确保 Blob Gas 机制按协议规则更新，防止费用操纵。

3. 区块头验证（Header Validation）
关键检查项：

区块高度：current_block.number = parent_block.number + 1。

时间戳：current_block.timestamp > parent_block.timestamp。

难度值（PoW 下）：需符合 Ethash 算法；但在 PoS 后，此字段可能固定。

共识规则：如 base_fee 是否符合 EIP-1559 规则。

意义：确保新区块头与父区块无缝衔接，符合协议共识。

4. 验证 Ommers 字段为空
背景：以太坊从 PoW 转向 PoS（The Merge）后，叔块（Ommers/Uncles）机制被废弃。

操作：检查当前区块的 ommers 字段必须为空列表 []。

意义：防止无效的叔块引用，维护 PoS 安全性。

5. 执行区块内的交易（Block Execution）
过程：逐笔执行区块中的交易，更新全局状态。

输出结果：

Gas Used：所有交易消耗的总 Gas，必须 ≤ 区块的 gas_limit。

Trie Roots：

transactions_root：交易树的根哈希。

receipts_root：收据树的根哈希。

state_root：执行后全局状态的根哈希。

Logs Bloom：所有交易日志的布隆过滤器，用于快速查询。

State：执行后的最新世界状态（账户余额、合约存储等）。

意义：交易执行是状态转换的核心，决定新区块的有效性。

6. 验证区块头参数（Header Parameters Verification）
关键校验：

state_root：必须与执行后的状态树根哈希一致。

transactions_root 和 receipts_root：必须与交易/收据树的根哈希匹配。

gas_used 和 logs_bloom：需与执行结果一致。

意义：确保区块头如实反映交易执行结果，防止数据篡改。

7. 添加区块到链（Block Addition）
操作：通过所有检查后，将新区块添加到区块链末尾。

意义：完成一次有效的状态转换，区块链长度 +1。

8. 修剪旧区块（Pruning Old Blocks）
背景：为优化存储，执行层通常仅保留最近 255 个区块的完整状态（非归档节点）。

操作：删除超过此范围的旧区块数据（但保留区块头）。

例外：归档节点会保留全部历史数据。

9. 错误处理（Error Handling）
失败场景：任何步骤校验不通过（如 Gas 超限、根哈希不匹配）。

操作：立即终止处理，抛出 Invalid Block 错误，区块不被加入链。

意义：确保无效区块不会破坏链的一致性或安全性。

状态根哈希（State Root）：全局状态的默克尔树根哈希，任何状态变化都会改变根哈希。

布隆过滤器（Logs Bloom）：高效存储日志事件的概率数据结构，便于轻节点快速过滤日志。

默克尔树（Merkle Trie）：以太坊用改进的默克尔帕特里夏树（MPT）存储账户、交易和收据。



<!-- Content_END -->
