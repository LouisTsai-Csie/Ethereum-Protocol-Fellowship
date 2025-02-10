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

### 2025.02.08

###  主题：Ethereum 共识层（Consensus Layer, CL）

####  主要内容
今天的学习重点是 **Ethereum 共识层（Consensus Layer, CL）**，它负责以太坊网络的安全性、数据一致性以及区块共识机制。主要涉及以下方面：

#### 共识层概述
- 区块链保证了 **数字稀缺性（Digital Scarcity）**，但需要 **安全性** 来确保其完整性。
- 分布式网络需要 **拜占庭容错（Byzantine Fault Tolerance, BFT）** 来应对恶意节点。
- **比特币（Bitcoin）** 通过 **工作量证明（Proof-of-Work, PoW）** 解决了 BFT 问题。
- **以太坊（Ethereum）** 通过 **权益证明（Proof-of-Stake, PoS）** 作为新共识机制。

#### PoS 机制
- PoS 由 **信标链（Beacon Chain）** 管理，并使用 **验证者（Validators）** 进行区块提议和投票。
- **从 PoW 转向 PoS 的关键变化：**
  - 由 **计算能力（哈希算力）** 转向 **代币抵押（Stake）** 作为 **反女巫攻击（Sybil Protection）** 机制。
  - 通过 **BFT 机制** 确保网络达成一致。
  - 参与 PoS 需要 **质押 32 ETH**，被选中的验证者负责出块和投票。

#### 拜占庭容错与 Slashing
- 以太坊 PoS 采用 **拜占庭容错（BFT Majority）** 来决定链的状态。
- 如果验证者行为异常或恶意，则会触发 **Slashing（削减惩罚）**：
  - **部分 Slash**：轻微违规，如错误投票，扣除部分质押。
  - **完全 Slash**：严重违规，如双重签名，导致全部 ETH 被销毁并被逐出网络。

#### Fork Choice Rule: LMD-GHOST
- 以太坊 PoS 使用 **LMD-GHOST（Latest Message Driven - Greedy Heaviest Observed Subtree）** 作为 **分叉选择规则（Fork Choice Rule）**：
  - **最新投票驱动**（Latest Message Driven）：最新投票更具权重。
  - **贪心最重子树**（Greedy Heaviest Observed Subtree）：选择投票最多的链作为主链。
  - **保证活跃性（Liveness）**：结合 **Casper FFG** 确保网络不会停滞。

#### 以太坊的加密经济安全性
- **Casper** 提供了更强的经济安全性：
  - 质押 ETH 提供了 **经济安全保证**，攻击者必须承担高额成本。
  - **双重签名 = 资金被 Slash**，确保验证者不会作恶。

### 2025.02.09

### 主题：开发和测试（Development and Testing）

#### 主要内容
本周的重点是以太坊的 **开发和测试**，包括如何进行节点的开发与测试、如何确保系统的稳定性和安全性等。

#### 开发概述
- **开发环境设置**：确保每个参与者的开发环境一致是关键，使用容器化（如 Docker）或虚拟机（VM）来模拟以太坊节点环境。
- **工具链**：常用的开发工具包括 **Go-Ethereum（Geth）** 和 **Besu** 等，以太坊的客户端实现；此外，**Hardhat** 和 **Truffle** 也常用于开发和测试智能合约。
- **智能合约开发**：了解如何在以太坊网络上部署和交互，重点是与 EVM 进行交互的能力。

#### 测试
- **自动化测试**：使用工具（如 **Ganache**、**Hardhat Network**）进行本地链测试，确保代码和智能合约的稳定性。
- **E2E 测试**：从区块链网络的端到端进行测试，模拟整个以太坊网络和应用的交互，以便测试其是否能正常运行。

#### 安全性
- **智能合约安全**：通过静态分析工具（如 **MythX**、**Slither**）来扫描合约中的漏洞。
- **攻击模型**：理解可能的攻击类型，如 **重入攻击（Reentrancy）**、**时间戳依赖性**、**整数溢出（Overflow）** 等，并采取相应的防护措施。

#### 测试实例
- **覆盖率测试**：测试合约的各个功能，确保所有可能的路径都被测试覆盖。
- **模拟真实场景**：使用 **测试网（Testnets）** 和 **正式网（Mainnet）** 的相同配置和行为来模拟真实场景，确保应用程序的稳定性。

<!-- Content_END -->
