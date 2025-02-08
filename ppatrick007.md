---
timezone: Asia/Shanghai
---
# {Patrick}

1. 自我介绍
Hi, 我是国内一名理科研究生，会一些编程语言，平时科研主要也是写程序算东西，
自学过一些前端、后端、服务器运维等知识（每次用还得去查一堆代码的程度，不过有了AI之后好了许多）

对区块链技术很感兴趣，希望学习到硬核的知识。

3. 你认为你会完成本次残酷学习吗？ Yes.
4. TG 联系方式：@ppatrick007

## Notes

<!-- Content_START -->

### 2025.02.06

### 今日学习主题：Ethereum —— The World Computer
- **Ethereum 是世界计算机**
  - 以太坊（Ethereum）是一种去中心化计算平台，为全球提供可信、开放、可编程的计算环境。
  - 由 **Ethereum Virtual Machine (EVM)**、**Ethereum Blockchain** 和 **Ethereum Network** 三部分组成。

- **以太坊共识机制**
  - 早期采用 **Proof of Work (PoW)**，2022年成功切换至 **Proof of Stake (PoS)**。
  - 使用 32 ETH 即可成为验证者（Validator），同时有 **Slashing（惩罚机制）** 来保证网络安全性。

- **去信任化（Trustless Trust）**
  - 以太坊的核心目标是 **可信中立（Credible Neutrality）**。
  - 通过 PoS 及去中心化架构实现全球无须信任的协调机制。

- **DeFi 及以太坊生态**
  - 以太坊支持 **去中心化金融（DeFi）**，让用户能够拥有 **互联网原生的财产所有权**。
  - 未来可能拓展至 **NFT、游戏、投票、物流** 等多种应用场景。

- **以太坊的扩展性挑战**
  - 目前以太坊面临 **扩展性三难困境（Scalability Trilemma）**，在 **安全、去中心化、扩展性** 之间需要权衡。
  - **Rollups** 和 **Danksharding** 可能是未来解决方案，提高吞吐量的同时保持去中心化。

### 2025.02.07

### 主题：Ethereum 执行层（Execution Layer）

#### 主要内容
今天的学习主要根据去年EPFsg的week2内容，重点是 **Ethereum 执行层（Execution Layer, EL）**，它负责处理交易、执行智能合约并维护以太坊的状态。主要涉及以下方面：

#### 执行层概览
- 负责处理状态转换（State Transition）。
- 验证并执行每一笔交易，将其累积到状态树（State Trie）。
- 处理以太坊改进提案（EIP）相关的机制，如：
  - **EIP-1559**: 交易基础费用调整机制。
  - **EIP-4844**: 处理 Blob Gas 以提高扩展性。
  - **信标链提款（Beacon Chain Withdrawals）**。

#### 区块验证（Block Validation）
- 执行层需要验证每个区块：
  - **头部验证（Header Validation）**：
    - 校验 **Merkle Root**。
    - 确保 **Gas Limit** 在合理范围内。
    - 确保时间戳有效。
  - **区块处理（Block Processing）**：
    - 通过 `state_processor.go` 执行状态转换。

#### EVM 及其操作码
- 以太坊虚拟机（EVM）是基于 **堆栈（Stack Machine）** 的计算环境。
- 主要操作码类别：
  - **栈/内存操作（Stack & Memory Manipulation）**。
  - **环境获取（Env Getters）**。
  - **以太坊系统操作（Ethereum System Operations）**。

#### P2P 网络 & 同步机制
- 以太坊的 **P2P 网络** 负责：
  - **提供历史数据**。
  - **广播待处理交易**。
  - **管理状态同步**。
- **Snap Sync 机制**：
  - **第一阶段：下载 Snap Tiles**（快速获取区块状态）。
  - **第二阶段：Healing**（填补数据缺失）。

#### JSON-RPC 及 Engine API
- JSON-RPC 是 **与以太坊交互的主要接口**，目标是所有客户端提供一致 API。
- 主要 RPC 方法：
  - `eth_getBlockByNumber`
  - `eth_call`
  - `eth_sendTransaction`
  - `eth_subscribe`

<!-- Content_END -->
