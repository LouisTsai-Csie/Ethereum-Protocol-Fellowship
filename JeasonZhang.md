# Jeason Zhang

1. 自我介绍：大家好，我是 Jeason Zhang，以太坊爱好者，全栈工程师，独立开发者，很开心参加今年的 EPF 残酷共学。
2. 你认为你会完成本次残酷学习吗？会的！

## Notes

<!-- Content_START -->

### 2025.02.06

今天是残酷共学的第一天，参加了 chloe 主持的第一周周会，会后看了一下[ epf wiki ](https://epf.wiki/#/eps/week1)中的内容，并用 deepseek - R1 总结了一下内容如下：

#### **I. 核心学习目标**

**主题**：以太坊协议基础与研发生态全景
 **目标**：理解以太坊设计哲学、技术架构、开发流程及社区协作模式。

------

#### **II. 核心学习模块**

##### **1. 历史与哲学基础**

- **UNIX哲学**
  - **核心理念**：模块化、简洁性、协作开发
  - 推荐资源
    - [UNIX纪录片](https://www.youtube.com/watch?v=tc4ROCJYbm0)（贝尔实验室文化）
    - [UNIX历史解析](https://www.theregister.com/2024/02/16/what_is_unix/)
- **自由软件运动**
  - **关键人物**：Richard Stallman（GNU项目）
  - **核心原则**：用户自由（运行、研究、修改、分发）
  - 必读材料
    - [自由软件定义](https://www.gnu.org/philosophy/free-sw.html)
    - 《大教堂与集市》（[在线版](http://www.catb.org/~esr/writings/cathedral-bazaar/)）
- **密码朋克与加密无政府主义**
  - **核心思想**：去中心化、隐私保护、密码学驱动自治
  - 经典文献
    - [密码朋克宣言](https://activism.net/cypherpunk/manifesto.html)
    - [加密无政府主义宣言](https://activism.net/cypherpunk/crypto-anarchy.html)
    - [网络空间独立宣言](https://www.eff.org/cyberspace-independence)

------

##### **2. 以太坊协议设计**

- **设计原则**
  - **五大核心**：简洁性、通用性、模块化、非歧视性、敏捷性
  - 技术文档
    - [以太坊黄皮书](https://ethereum.github.io/yellowpaper/)（数学化协议定义）
    - [执行层规范](https://github.com/ethereum/execution-specs)（Python实现）
- **网络架构**
  - 分层结构
    - **执行层（EL）**：处理交易与智能合约（EVM）
    - **共识层（CL）**：PoS机制与区块确认
  - **节点类型**：全节点、轻节点、归档节点
  - 扩展阅读
    - [节点架构文档](https://ethereum.org/developers/docs/nodes-and-clients/)
    - [路线图解析](https://ethereum.org/roadmap)

------

##### **3. 实现与开发**

- 客户端多样性
  - **执行层客户端**：Geth、Nethermind、Besu
  - **共识层客户端**：Lighthouse、Prysm、Teku
  - **开发语言**：Go、Rust、Java、C#等
  - 资源
    - [客户端列表](https://ethereum.org/developers/docs/nodes-and-clients/#execution-clients)
    - [EPF项目案例](https://github.com/eth-protocol-fellows/cohort-four)

------

##### **4. 测试与安全**

- **测试工具链**
  - 核心仓库
    - [通用测试集](https://github.com/ethereum/tests)
    - [Retesteth工具](https://github.com/ethereum/retesteth)（状态转换测试）
    - [Hive测试框架](https://github.com/ethereum/hive)（多客户端仿真）
  - **测试类型**：单元测试、模糊测试、影子分叉
- **安全实践**
  - **漏洞赏金计划**：通过[HackerOne](https://hackerone.com/ethereum)提交
  - **代码审计**：形式化验证（如[KEVM](https://github.com/kframework/evm-semantics)）

------

##### **5. 社区协作机制**

- **协调流程**
  - 核心会议
    - **ACD会议**（All Core Devs）：双周例会
    - **PM仓库**（[ethereum/pm](https://github.com/ethereum/pm)）记录议程
  - **提案流程**：EIP（[EIPs仓库](https://github.com/ethereum/EIPs)）
- **讨论平台**：
  - [EthResearch论坛](https://ethresear.ch/)（技术研究）
  - [Ethereum Magicians](https://ethereum-magicians.org/)（提案讨论）
  - **R&D Discord**（需邀请）

------

#### **III. 学习路径建议**

##### **1. 入门阶段**

- **视频学习**：
  - [Mario Havel讲座](https://streameth.org/ethereum-protocol-101)（以太坊协议基础）
  - [Richard Stallman演讲](https://www.youtube.com/watch?v=Ag1AKIl_2GM)（自由软件理念）
- **基础阅读**：
  - [以太坊30分钟入门](https://ethereum.org/learn/)
  - [绝对以太坊精要](https://www.amazon.com/Absolute-Essentials-Ethereum-Matt-Garnett/dp/1119893410)（新书推荐）

------

##### **2. 技术深化**

- **实践任务**：
  - **运行测试网节点**：使用Geth + Lighthouse组合
  - **参与测试**：通过[Hive](https://github.com/ethereum/hive)提交客户端兼容性报告
- **代码研读**：
  - 分析[执行层规范](https://github.com/ethereum/execution-specs)中的状态转换逻辑
  - 研究[EIP-1559](https://eips.ethereum.org/EIPS/eip-1559)实现代码

------

##### **3. 社区参与**

- **跟踪开发动态**：
  - 订阅[ACD会议纪要](https://github.com/ethereum/pm)
  - 加入[EPF Discord](https://discord.gg/eth-protocol-fellows)参与讨论
- **贡献方式**：
  - 提交EIP改进提案
  - 参与[ETHGlobal黑客松](https://ethglobal.com/)

------

#### **IV. 扩展资源**

- **书籍推荐**：
  - 《The Infinite Machine》（以太坊早期史）
  - 《Mastering Ethereum》（技术细节解析，需注意版本）
- **高级学习**：
  - [Devcon演讲存档](https://archive.devcon.org/)（技术深度内容）
  - [形式化验证案例](https://github.com/ethereum/aleth)（Aleth项目）

------

#### **V. 学习评估**

- 自测工具
  - [以太坊基础知识测验](https://ethereum.org/quizzes)
  - 编写简单智能合约并通过[执行层测试](https://github.com/ethereum/execution-spec-tests)验证

笔记内容

### 2024.02.07

#### **I. 核心学习目标**

**主题**: 以太坊执行层（Execution Layer）深度解析
 **目标**: 掌握执行层节点架构、状态转换机制、EVM运行原理及网络通信协议。

------

#### **II. 课程大纲重点**

##### **1. 执行层节点架构**

- **区块验证（Block Validation）**：
  - 处理状态转换（State Transition），将交易结果记录到**状态树（Merkle Patricia Trie）**
  - 维护动态机制更新：EIP-1559基础费用、EIP-4844 Blob Gas、信标链提款等
  - 提供**快速同步机制**（Snap Sync）帮助新节点快速接入网络
- **区块构建（Block Building）**：
  - 基于P2P交易池（Tx Pool）构建新区块
  - 交易广播与验证的双向流程

##### **2. 状态转换函数**

- 区块头验证：
  - 校验**默克尔根**（交易根、状态根、收据根）
  - 验证Gas限制与时间戳合法性
- 区块验证代码实践：
  - 分析[go-ethereum代码库](https://github.com/ethereum/go-ethereum)中`core/state_processor.go`的`Process()`函数

##### **3. EVM运行机制**

- 栈式虚拟机原理：
  - 操作码分类解析：
    - 堆栈操作码（如`PUSH`, `POP`）
    - 内存操作码（如`MLOAD`, `MSTORE`）
    - 系统级操作（如`CALL`, `DELEGATECALL`）
- 实战工具推荐：
  - [evm.codes](https://www.evm.codes/)：交互式EVM操作码解析工具
  - [ethervm.io](https://ethervm.io/)：EVM指令集速查表

##### **4. P2P网络协议**

- 三大核心功能：
  - 历史区块数据传输
  - 未确认交易（Pending Transactions）广播
  - 状态数据同步
- Snap Sync技术：
  - **阶段一**：下载快照数据块（Snapshot Tiles）
  - **阶段二**：状态修复（State Healing）

##### **5. JSON-RPC接口**

- 设计目标：
  - 统一所有客户端的API标准，实现工具链无缝集成
  - 目前接近实现但仍有细微差异
- 关键RPC方法：
  - `eth_getBlockByNumber`
  - `eth_sendRawTransaction`
  - `eth_call`

------

#### **III. 核心学习资源**

##### **必读材料**：

- [执行层规范](https://github.com/ethereum/execution-specs)（Python实现）
- [ETH2术语更新说明](https://blog.ethereum.org/2022/01/24/the-great-eth2-renaming)
- [合并对应用层的影响](https://blog.ethereum.org/2021/11/29/how-the-merge-impacts-app-layer)

##### **进阶工具**：

- [Engine API可视化指南](https://hackmd.io/@danielrachi/engine_api)（Daniel Ramirez）
- [Lightclient开发环境配置](https://github.com/lightclient/dotfiles)

##### **代码研究**：

- 核心代码库：
  - [go-ethereum](https://github.com/ethereum/go-ethereum)
  - [devp2p协议](https://github.com/ethereum/devp2p)
- 执行层API规范：
  - [execution-apis](https://github.com/ethereum/execution-apis)

------

#### **IV. 学习实践建议**

1. **代码调试**：在本地运行Geth节点，观察`state_processor.go`的区块处理流程
2. **网络模拟**：使用[devp2p工具包](https://github.com/ethereum/devp2p)模拟P2P交易广播
3. **RPC实验**：通过Postman调用JSON-RPC接口获取链上数据

### 2025.02.08

<!-- Content_END -->
