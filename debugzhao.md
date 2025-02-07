---
timezone: Asia/Shanghai
---

# Tyson

1. 自我介绍：大家好，我是Tyson，web3爱好者, 很高兴再次参加残酷共学
2. 你认为你会完成本次残酷学习吗？会的！

## Notes

<!-- Content_START -->

### 2025.02.06

刚开始接触EPF，快速浏览了一下wiki文档。EPF Wiki 是有关 Ethereum 协议的技术资源的集合。它是 EPF 研究组和协议 Wiki 的所有资源的所在地。

参与了[2025  participant survey](https://docs.google.com/forms/d/e/1FAIpQLSf4W3R5LZnUIqXpAw2MwJ4E4Q_YWf9tv-BlR5w8v9ED5LjBjw/viewform)，并了解到EPS，EPS学习小组内容分为两个阶段 - 密集的介绍和深入的探讨。前 2 周包括学习[前一个学习小组](https://epf.wiki/#/eps/SG2024)的现有课程。接下来的 6 周将提供来自核心开发人员和研究人员的新现场讲座，其中的材料涵盖以太坊的执行层和共识层的各个部分。

#### [Prehistory and Philosophy](https://epf.wiki/#/eps/week1?id=prehistory-and-philosophy)

非对称密码学的发明意味着密码学新范式的诞生，保证了数字隐私、安全通信，并从根本上改变了网络安全，也成了加密货币基本组成部分。

#### [Ethereum Protocol Design](https://epf.wiki/#/eps/week1?id=ethereum-protocol-design)

以太坊最初在其[白皮书](https://ethereum.org/whitepaper#ethereum-whitepaper)中进行了概述，它从比特币及其背景（如上所述）中汲取灵感，创建了一个基于区块链的通用计算平台。该设计在[黄皮书](https://ethereum.github.io/yellowpaper/paper.pdf)中进行了技术说明，并随着时间的推移而发展。

协议最大的特点：**简单、通用、模块化、无歧视、敏捷**

核心生态系统是一个不断生长的[无限花园](https://ethereum.foundation/infinitegarden)。然而，随着越来越多的进展，以太坊可能会慢慢接近僵化。

### 2024.02.07

1. **以太坊虚拟机（EVM）深入解析**
   - **EVM 架构**：解释堆栈式虚拟机的工作原理，包括操作码（Opcode）、执行环境、内存模型。
   - **合约执行流程**：从字节码编译到部署，以及交易触发合约函数时的状态变化。
2. **Gas 机制与优化**
   - **Gas 计算规则**：不同操作（如存储写入、数学运算）的 Gas 消耗标准。
   - **优化策略**：减少合约 Gas 成本的技巧，例如避免冗余存储、使用更高效的数据结构。
3. **状态管理与默克尔树**
   - **全局状态树**：以太坊如何通过 Patricia-Merkle 树管理账户和合约状态。
   - **存储结构**：合约内部存储的键值对布局及其哈希表示。
4. **交易生命周期**
   - **交易池（Mempool）**：交易从提交到被打包进区块的流程。
   - **验证与执行**：节点如何验证交易有效性（签名、GasLimit 等）。
5. **开发工具与实践**
   - **Solidity 进阶**：内联汇编（Inline Assembly）的使用场景与风险。
   - **调试工具**：利用 Remix、Hardhat 或 Tenderly 跟踪 EVM 执行过程。

<!-- Content_END -->
