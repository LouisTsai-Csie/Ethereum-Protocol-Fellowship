---
timezone: Asia/Shanghai
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# Ray

1. 自我介绍
LXDAO builder，正在做 [PGNode](https://pgnode.xyz/)，正在持续深入研究以太坊
2. 你认为你会完成本次残酷学习吗？
会的

## Notes

<!-- Content_START -->

### 2025.02.06

填写了 Survey 2025：https://docs.google.com/forms/d/e/1FAIpQLSf4W3R5LZnUIqXpAw2MwJ4E4Q_YWf9tv-BlR5w8v9ED5LjBjw/viewform

整个 Wiki 在第一次残酷共学的时候已经看过了一遍，这次相当于重新复习一下。

#### 如何使用这份资料
这份资料对于想深入研究以太坊协议的人来说非常棒，可以完整系统的学习以太坊协议层的内容：

- 想深入了解以太坊协议的细节，仔细阅读 `Execution Layer` 和 `Consensus Layer` 两个章节，里面的内容比以太坊官方的文档更加深入
- 想了解以太坊简史及设计理念，阅读 `The Protocol` 章节，里面介绍了以太坊的设计理念和发展简史
- 想了解以太坊的开发模式，阅读 `Development` 和 `Testing and security` 等章节，其中 `Development` 中的 `Dev Resources` 中整理了参与以太坊协议开发需要储备的知识，非常贴心了
- 关于以太坊当前正在进行的前沿研究，阅读 `Research`
- Study Group 2024 中是之前的学习笔记，偏实践，也很值得阅读

#### 对以太坊协议发展的理解
很多人总把以太坊和 BTC 放在一起比较，但其中这两个项目本质上的发展路径是不一样的：
- BTC：诞生就是完全体，协议本身没有做迭代的计划，更多的是安全性的优化和抗量子方面的考量
- Ethereum：初始是一个半成品，一开始就有迭代计划，目前离完全体还有很长的路要走

所以在以太坊的发展过程中，会持续有新的话题产生。因为随着技术的迭代，之前的规划很多都会作废，需要有新的方案诞生，然后继续实现，然后出现新的问题，然后继续解决问题。这会成为以太坊发展过程中的常态。

相比与最初的版本，当前以太坊的协议已经很复杂了，协议复杂化的解决方案就是模块化，The Merge 升级之后，以太坊就已经分成了两个大的模块，后续可能会拆分成更多的模块。模块化的好处很明显，可以封装复杂性，不同模块之间通过 API 来通信，模块内部的实现可以自行迭代，不同模块之间互不影响。确定也很明显，模块增加，理解成本增加，以后可能很难找到一个人能真正完整理解以太坊。

模块化还会带来另外一个问题，以太坊节点的部署难度会增加，而且随着以太坊的发展，节点的种类会越来越多，那么节点的部署门槛可能就会增加，solo-staking 的比例就会不够，这可能会对以太坊的安全性有害，[PGNode](https://pgnode.xyz/)，正在尝试解决这个问题，降低节点的部署门槛。

以太坊的路害很长，还有很多事情可以做，持续 Building。

### 2025.02.07
以太坊之前的[黄皮书](https://ethereum.github.io/yellowpaper/paper.pdf)已经过期了，现在以太坊协议已经拆分成了两个规范，[执行层规范](https://github.com/ethereum/execution-specs)和[共识层规范](https://github.com/ethereum/consensus-specs)。

在拆分之前，以太坊客户端既负责交易的执行、传播，也负责网络共识的达成，在拆分之后，共识层剥离成为单独的共识层，原来的客户端也就成了纯粹的执行层。在拆分之后，执行层和共识层的所承载的功能大致如下：
- 执行层
    - 交易池
    - 状态存储
    - 区块和交易的执行（STF）
    - EVM
- 共识层
    - 共识模块（Gasper = Casper-FFG + LMD-GHOST）
    - 最新区块同步
    - Blob 数据存储
    - Validator 交互

关于执行层和共识层所需要知道的一些事情：
- 执行层和共识层都又自己的 p2p 网络，执行层的 p2p 网络主要用来传播和接收交易，共识层的 p2p 网络主要用来同步最新区块和 blob 数据
- 一个执行层客户端只能连接一个共识层，而共识层可以连接多个执行层和多个 Validator
- 与此同时 Beam Chain 项目也立项了，准备对共识层进行重构，并将大量应用 ZK 技术，没有在当前的共识层上设计是为了减轻技术负债的负担，可以面向未来重新出发，这也是模块化的好处，只要共识层和执行层之间的 API 不变，就可以在模块内部重新设计并开发，而且对于共识层来说，大多数数据是只需要存储一段时间，大多数数据过期之后可以不用存储，对数据兼容性的处理的负担也会比较小


经过这几年的发展，以太坊的客户端多样性得到了很大的提升，越来越多新的客户端被开发出来，Geth 不再是唯一的选择了，其中有个趋势是，使用 rust 开发的的客户端越来越多，其实这也好理解，因为这些客户端始终是运行在单机上的，客户端需要处理的数据和请求越来越多，使用 rust 会将机器的能力发挥的更好，rust 开发或许是一个趋势。


### 2025.02.08

执行层的核心是 EVM，如果把整个以太坊协议看作是**交易驱动的状态机（transaction-based state machine）**，那么 EVM 就是其中的 STF（State transition function），状态机有三个重要的组成部分：
- State
- Inputs
- State transtion function

State 就对应了**世界状态**，Inputs 就对应了**交易**，STF 对应 EVM，可以说这三个才是以太坊协议的核心，其他的组件都是为这三个核心服务的，保证交易能够在 EVM 上正常执行，然后交易带来的变更能够写入世界状态。区块链记录了所有交易执行的过程，这样任何一个节点的世界状态也都是一致的，也无法篡改，而共识层所做的事情就是为了新区块的产生是有序的，新区块的产生是更新世界状态的唯一途径。

但是由于整个以太坊网络是公开的，所以通过 gas 来限制恶意的攻击以及实现按照市场的方式让用户付出对应的成本来来使用以太坊，gas 机制的存在让用户提交的交易在以太坊上执行的次数是有限制的，因此 EVM 被认为是准图灵完备（quasi Turing complete）的。

在初始阶段，以太坊是执行层和共识层在同一个客户端中，完成在 The Merge 升级之后，以太坊分成了两个客户端，**执行层客户端**和**共识层客户端**，这样有好处也有坏处：

坏处：
- 失去了一个简单的共识规则，共识规则变得很复杂
- 失去了真正意义上的 permissionless

好处：
- 减少了能源的消耗
- 带来了更好的可塑性，比如 blob 交易的实现

在分开之后，以太坊构造区块的过程也是由共识层和执行层配合完成，如果 validator 被选中在 slot 中创建区块之后，就会向共识层客户端要求获取区块，共识层客户端就会调用执行层客户端的 fork choice updated API 来生成区块。

共识层在获取到新的区块信息之后，也会传递给执行层客户端，执行层客户端会验证区块头信息是否合法，确认没问题之后就会执行区块中的交易，然后将区块附加到区块链上。

### 2025.02.09

EVM 是为了屏蔽底层操作系统和硬件的差异而创建，这样应用层的代码就可以统一，只需要为 EVM 写一遍，类似Java 中的 JVM。

EVM 中有一些关键的组件：

- EVM bytecode：字节码是将程序表示为一系列的字节（byte），每个字节都表示如下的含义，为了简单，每个字节都是用 16 进制表示：
    - 一个指令（opcode），为了进一步增强理解，把操作码抽象层人类可读的形式，比如 PUSH1，这种简化的字节码称之为 EVM assembly（EVM 汇编）
    - 指令的输入，操作数（operand）
- EVM stack：EVM 的字节码的操作是在一个 stack 中进行的，stack 最大为 1024，如果超出这个范围，就会报 stack underflow error
- Program counter：表示指令的偏移量，表示下一个指令开始的位置
    - JUMP：改变程序计数器的值，从而实现控制流
    - JUMPDEST：标记一个有效的跳转目的地，当 JUMP 执行时，它所跳转的目标位置必须被 JUMPDEST 标记过，JUMPDEST 会标记每个循环的开始位置以及不同条件分支的入口
- Memory：是一个长度为 2^256 次方的字节数组，内存中的初始值都定义为 0，与 EVM 搭配使用
    - 字（Word）与字节（Byte）的区别
        - Byte 就是一个字节，等于 8 位
        - 计算机进行数据处理时，一次存取、加工和传送的数据长度，在不同的计算机系统中可能不同，常见的字长有8 位、16位、32位、64位，比如在 32 位的计算系统中，一个字就是 32 位，也就是 4 个字节
- Storage：EVM 执行的结果都需要写入到 stroage 中，storage 与以太坊地址相关联，并作为世界状态的一部分永久保存，storage 只能通过关联的代码才能访问，EOA 没有代码，因此无法访问自己的 storage

<!-- Content_END -->
