---
timezone: Asia/Shanghai
---

# Oscar

1. A eco-lifelong learner. To surf🏄‍♀️ better in the Web3 world. Enjoy this challenging vibe and become cooler 🆒. TG：lessaremore
2. 你认为你会完成本次残酷学习吗？ Yes. 

## Notes

<!-- Content_START -->
### 2025.02.06
**学习主题：此次共学内容 EPF 背景，及内容方向**
学习了解 https://epf.wiki/ ，initiated by EF Protocol Support and maintained by EPFsg community. 主要搞清楚EF、EPF、EPFsg community 间关系。
- EPFsg has been designed to guide and grow the next generation of Ethereum core developers and provide a deep understanding of Ethereum's internal mechanics. 
- EPF Wiki 是一个关于以太坊协议的技术资源中心。focused on a general overview of the underlying structure of Ethereum. 此 Wiki 的范围仅限于以太坊核心协议基础设施的技术资源。

EPF 学习小组是一个实时网络研讨会式项目，由两个阶段组成。第一阶段，每周将有一节 90 分钟的课程，重点介绍以太坊底层结构的一般概述。在后期阶段，学生将选择研究或开发方向（或两者）。深入研究的主题包括：
- Protocol design 
- Execution and Consensus layer architecture, specs, and implementations 执行和共识层架构、规范和实现
- Testing methods and tools 
- Current research and roadmap items: 
    - Verkle trees
    - Sharding
    - MEV
    - Proof of stake improvements
    - State and history expiry

### 2025.02.07
**学习了解 ETH 早期历史：**
- 根植于早期互联网的开放精神，并受到几个关键运动和技术的影响。它从 Unix 的简洁性和模块化设计理念、GNU/Linux 所体现的自由和开源运动以及密码朋克所倡导的密码学进步中汲取灵感。

- 互联网本身起源于 ARPANET，它连接了世界，打破了地域障碍，实现了前所未有的互动。 Unix 及其 C 语言为软件设计提供了基本原则，强调简洁性和可重用性。 出于对安全通信的需求而诞生的公钥密码学为无需信任的系统铺平了道路。 

- 由 Richard Stallman 和 GNU 项目领导的自由软件运动强调自由高于价格，从而产生了 GNU/Linux 操作系统。 这凸显了协作式、社区驱动的软件开发的强大力量。

- 密码朋克寻求一种密码学上安全的数字货币，从而促成了 DigiCash、B-money 和 BitGold 等尝试。 虽然这些努力没有成功，但它们为比特币的设计提供了信息。 

👍 比特币也是世界上有史以来最大的社会经济实验。中本聪于 2009 年 1 月首次启动比特币区块链时，他同时引入了两个激进且未经测试的概念。 第一个是“比特币”，一种去中心化的点对点在线货币，无需任何支持、内在价值或中央发行机构即可维持价值。 另一个同样重要的部分是：基于工作量证明的区块链的概念，以允许公众对交易顺序达成一致。
- 中本聪的比特币引入了一种去中心化的点对点电子现金系统，但其在应用程序开发方面的局限性导致了以太坊的出现。

- Bitcoin Magazine 的联合创始人 Vitalik Buterin 认识到比特币的局限性，并提出了一个更通用的平台。 在 Gavin Wood 的帮助下，以太坊的设计得以正式确定，并于 2015 年 7 月 30 启动，旨在构建一个自主的数字经济。On July 30, 2015, Ethereum went live as a platform aimed at building tools for a self-sovereign economy using digital currency. 其目标是构建一个无国界、自我主权的数字经济生态。

### 2025.02.08
学习了解 ETH 协议架构 epf.wiki/#/wiki/protocol/architecture

**协议发展与目前构架：**
- 当前的协议架构是多年发展的成果。该协议由两个主要部分组成 - 执行层和共识层。
- 执行层 (EL) 处理实际的交易和用户交互，它是 the global computer 执行其程序的地方。
- 共识层 (CL) 提供权益证明共识机制 - 一种 cryptoeconomic security ，确保所有节点遵循相同的提示并驱动执行层的规范链。
- 在实践中，这些层是在其自己的客户端中实现的，这些客户端通过 API 连接。每个都有自己的 p2p 网络来处理不同类型的数据。

**分析：**
- 图显示了以太坊的模块化架构，将共识（就状态达成一致）与执行（运行智能合约和处理交易）的关注点分开，并允许将来的升级和可伸缩性改进。
- Engine API 充当桥梁，使两层可以协同工作以维护安全且一致的区块链。

**扩展学习：Blobs**
- 一种“半链下”解决方案，可在成本效率和数据安全性/可用性之间取得平衡。虽然 blobs 不是以与交易数据或状态数据相同的方式直接存储在以太坊区块链上，但它们是由以太坊网络管理和保证 的。
- 在 AI 辅助下梳理 Blobs workflow 图：仅供参考
- ![](img/blobs_workflow.png)
  

### 2025.02.09

**学习主题：Protocol Design Philosophy**
五个核心原则及其具体指导：
* Simplicity 简洁
    * Managing Complexity (sandwich model complexity & encapsulated complexity)
* Universality 通用基础
    * Generalization
    * We have no features 

* Modularity 模块
* Non-discrimination 无歧视性
    * Freedom 类似中立性
* Agility 敏捷


<!-- Content_END -->
