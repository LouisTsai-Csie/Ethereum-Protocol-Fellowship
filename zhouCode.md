---
timezone: Asia/Shanghai
---

# zhouCode

1. 自我介绍
    - zhou，高校网络安全专业教师，教授课程《系统安全》《网络内容安全》等
    - 近期学习以太坊协议，同时经过好友推荐发现 EPF study group，非常想加入共同学习一起进步！
    - 实践经验：轻度参与**D2PFuzz 模糊测试工具**的协议安全性验证（DevP2P协议族测试）
2. 你认为你会完成本次残酷学习吗？
    - 一定！

## Notes

<!-- Content_START -->

### 2025.02.06

#### 认识以太坊

- 主要内容：以太坊基本概念
- 关键词：以太坊协议、以太坊开发、以太坊测试、以太坊开发模式

#### 学习目标

- [x] 目标1：了解以太坊背景，起源和发展历程
- [x] 目标2：阅读相关条目及背景资料

#### 主要内容

##### 以太坊出现的必要条件

模块化、自由软件运动、非对称加密

##### 以太坊协议

灵感来自比特币，基本原则：简单、通用、模块化、无歧视、敏捷

以太坊协议还在不断完善和进步

主要分为2层：**执行层**(EL)、**共识层**(CL)

执行层提供执行动力，处理交易和状态

共识层包括权益证明机制，确保安全和纠错

##### 以太坊的实施和开发

执行层和共识层的实现称为**客户端**。运行此客户端并连接到网络的计算机称为**节点**。

因此，节点是一对积极参与网络的EL和CL客户端。

由于ETH只在形式上做规定，所以任何语言都可以实现

##### 以太坊测试

由于客户端有多个，所以安全测试也是必要的，有多种测试工具会被使用。

测试根据规范生成，并创建各类场景。有对单独客户端的测试，也有对多个客户端行程的网络的测试。

由此分出类型：状态转换测试(state transition testing)、模糊测试(fuzzing)、影子分叉(shadow forks)、RPC 测试(RPC tests)、客户端单元测试(client unit tests)和 CI/CD 等。

##### 合作模式

以太坊开发均为公开，不同团队负责不同部分

> 新功能或更改的传统开发周期是 `Idea - Research - Development - Testing - Adoption`

### 2025.02.07
#### study group 2024 week2 Pre-reading学习

- 主要内容：初步认识EVM，认识节点和客户端的概念，了解同步模式
- 关键词：EVM，节点，执行客户端，共识客户端，同步

#### 学习目标

- [x] 目标1：认识EVM
- [x] 目标2：认识节点和客户端
- [x] 目标3：认识同步模式

#### 主要内容

##### 内容1：以太坊虚拟机(Ethereum Virtual Machine)

![EVM 组成结构图](https://ethereum.org/_next/image/?url=%2Fcontent%2Ftranslations%2Fzh%2Fdevelopers%2Fdocs%2Fevm%2Fevm.png&w=1920&q=75)

##### 以太坊状态转换函数

EVM类似于函数，输入后会有确定输出。所以，以太坊——状态转换函数

```
Y(S, T)= S'
```

给定一个旧的有效状态 `（S）`> 和一组新的有效交易 `（T）`，以太坊状态转换函数 `Y（S，T）` 产生新的有效输出状态` S'`

###### 状态(State)

状态是一个巨大的数据结构，称为[修正的 Merkle Patricia Trie](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)，它保持所有[账户](https://ethereum.org/en/developers/docs/accounts/)通过哈希链接，并可简化为存储在区块链上的单个根哈希。

###### 交易(Transactions)

交易是来自帐户的密码学签名指令。

分为2种：**消息调用交易**，**合约创建交易**

合约创建交易会创建一个新的合约帐户，其中包含已编译的 [智能合约](https://ethereum.org/zh/developers/docs/smart-contracts/anatomy/) 字节码。 每当另一个帐户对该合约进行消息调用时，它都会执行其字节码。

##### EVM说明

EVM为一个堆栈机，栈深度为1024 item，每个item 是一个256位的word， 256方便使用256位的加密技术

运行过程中，EVM 维持一个瞬态内存（字可寻址字节数组），不会在交易间持久存在

合约中存在的是Merkle Patricia *storage* trie(MPT)，与账户关联，且是**全局状态的一部分**

已编译的智能合约字节码在执行时会调用多个 EVM 操作码（Opcode），这些操作码执行标准的栈操作，例如 XOR、AND、ADD、SUB 等。此外，EVM 还实现了一些特定于区块链的栈操作，例如 ADDRESS、BALANCE、BLOCKHASH 等。

![表明 EVM 操作需要 Gas 的图表](https://ethereum.org/_next/image/?url=%2Fcontent%2Fdevelopers%2Fdocs%2Fgas%2Fgas.png&w=1920&q=75)

##### EVM的实现

EVM 的所有实现都必须遵守以[太坊黄皮书](https://ethereum.github.io/yellowpaper/paper.pdf)中描述的规范。

以太坊虚拟机经过了几次修订，并且存在不同编程语言实现的以太坊虚拟机版本。

##### 内容2：节点和客户端

以太坊是一个**由计算机组成的分布式网络**，这些计算机运行**可验证区块**和**交易数据的软件**，称为**节点**。 该软件必须在你的计算机上运行，才能将其转化为以太坊节点。 **一个节点由两个独立的软件**（名为“客户端”）构成。

##### 节点和客户端

**节点**是指任何以太坊客户端软件的实例，它连接到其他也运行以太坊软件的计算机，形成一个网络。

**客户端**是以太坊的实现，它根据协议规则验证数据并保持网络安全。 

个节点需要运行两种客户端软件：共识客户端和执行客户端。

- 执行客户端（也称为执行引擎、EL 客户端或旧称“以太坊 1”客户端）侦听网络中广播的新交易，并在以太坊虚拟机中执行它们，并保存所有当前以太坊数据的最新状态和数据库。
- 共识客户端（也称为信标节点、CL 客户端或旧称“以太坊 2”客户端）实现权益证明共识算法，使网络能够根据来自执行客户端的经验证数据达成一致。 此外还有名为“验证者”的第三种软件，它们可被添加到共识客户端中，使节点能参与保护网络安全。

![关联执行和共识客户端](https://ethereum.org/_next/image/?url=%2Fcontent%2Fdevelopers%2Fdocs%2Fnodes-and-clients%2Feth1eth2client.png&w=1920&q=75)

关联执行与共识客户端的简化图

##### 客户端多样性

不同团队开发的各种编程语言中都有[执行客户端](https://ethereum.org/zh/developers/docs/nodes-and-clients/#execution-clients)和[共识客户端](https://ethereum.org/zh/developers/docs/nodes-and-clients/#consensus-clients)。

多种客户端实现减少了对于单一代码库的依赖，使网络更强大。

##### 跟踪网络中的节点

多种跟踪器提供以太坊网络中节点的实时概览。由于去中心化网络的性质，这些爬虫只能提供有限的网络视图，并且可能会报告不同的结果。

##### 节点类型

客户端可以运行三种类型的节点：**轻节点**、**全节点**和**归档节点**。

###### 轻节点（发展方向）

轻节点只下载区块头，而不会下载每个区块。这些区块头包含区块内容的摘要信息。

轻节点会向全节点请求其所需的任何其他信息。

轻节点可以让用户加入以太坊网络，无需运行全节点所需的功能强大的硬件或高带宽。 最终，轻节点也许能在手机和嵌入式设备中运行。 轻节点不参与共识（即它们不能成为矿工/验证者），但可以访问功能和安全保障和全节点相同的以太坊区块链。

以太坊目前还不支持大量轻节点，但轻节点支持是一个有望在不久的将来快速发展的领域。 特别是像 [Nimbus](https://nimbus.team/)、[Helios](https://github.com/a16z/helios) 以及 [LodeStar](https://lodestar.chainsafe.io/) 这样的客户端目前都非常关注轻节点。

###### 全节点

全节点对区块链进行逐块验证，包括下载和验证每个块的块体和状态数据。全节点只保留相对较新数据的本地副本（通常是最近的 128 个区块），允许删除比较旧的数据以节省磁盘空间。 旧数据可以在需要时重新生成。

特点：

- 存储全部区块链数据（会定期修剪，所以全节点并不存储包含创世块在内的所有状态数据）
- 参与区块验证，验证所有区块和状态。
- 全节点可以从本地储存中检索所有状态，或从“快照”中重新生成。
- 为网络提供服务，并应要求提供数据。

###### 归档节点

归档节点是从创世块开始验证每个区块的全节点，它们从不删除任何下载的数据。

特点：

- 存储全节点中保存的所有内容，并建立历史状态存档。 如果你想查询区块 #4,000,000 的帐户余额，或者想简单可靠地测试自己的一组交易而不使用跟踪挖掘它们，则需要归档节点。
- 这些数据以太字节为单位，这使得归档节点对普通用户的吸引力较低，但对于区块浏览器、钱包供应商和链分析等服务来说则很方便。

以归档以外的任何方式同步客户端将导致区块链数据被修剪。 这意味着，不存在包含所有历史状态的归档，但全节点能够在需要时构建它们。

##### 运行节点

对个人的优点：

以私密、自给自足的去信任方式使用以太坊。可以使用自己的客户端验证数据。*“不要信任，直接验证”*

![如何通过你的应用和节点访问以太坊](https://ethereum.org/_next/image/?url=%2Fcontent%2Fdevelopers%2Fdocs%2Fnodes-and-clients%2Fnodes.png&w=1920&q=75)

对网络的优点：

多样化的节点对于以太坊的健康、安全和运行弹性非常重要。

##### 运行节点的代替方法

可以使用第三方应用程序接口提供商。 有关使用这些服务的概述，请查看[节点即服务](https://ethereum.org/zh/developers/docs/nodes-and-clients/nodes-as-a-service/)。

##### 执行客户端

| 客户端                                                       | 语言       | 操作系统              | 网络                   | 同步策略         | 状态缓冲        |
| ------------------------------------------------------------ | ---------- | --------------------- | ---------------------- | ---------------- | --------------- |
| [Geth](https://geth.ethereum.org/)                           | Go         | Linux、Windows、macOS | 主网、Sepolia、Holesky | 快照、完全       | Archive、Pruned |
| [Nethermind](https://www.nethermind.io/)                     | C#、.NET   | Linux、Windows、macOS | 主网、Sepolia、Holesky | 快照、完全       | Archive、Pruned |
| [Besu](https://besu.hyperledger.org/en/stable/)              | Java       | Linux、Windows、macOS | 主网、Sepolia、Holesky | 快照、快速、完全 | Archive、Pruned |
| [Erigon](https://github.com/ledgerwatch/erigon)              | Go         | Linux、Windows、macOS | 主网、Sepolia、Holesky | 完全             | Archive、Pruned |
| [Reth](https://reth.rs/)                                     | Rust       | Linux、Windows、macOS | 主网、Sepolia、Holesky | 完全             | Archive、Pruned |
| [EthereumJS](https://github.com/ethereumjs/ethereumjs-monorepo) | TypeScript | Linux、Windows、macOS | Sepolia、Holesky       | 完全             | 修剪            |

##### 共识客户端

负责所有共识相关的逻辑，包括分叉选择算法、处理认证与管理[权益证明](https://ethereum.org/zh/developers/docs/consensus-mechanisms/pos/)奖励及惩罚。

| 客户端                                                       | 语言       | 操作系统              | 网络                                                 |
| ------------------------------------------------------------ | ---------- | --------------------- | ---------------------------------------------------- |
| [Lighthouse](https://lighthouse.sigmaprime.io/)              | Rust       | Linux、Windows、macOS | 信标链、Goerli、Pyrmont、Sepolia、Ropsten 等         |
| [Lodestar](https://lodestar.chainsafe.io/)                   | TypeScript | Linux、Windows、macOS | 信标链、Goerli、Sepolia、Ropsten 等                  |
| [Nimbus](https://nimbus.team/)                               | Nim        | Linux、Windows、macOS | 信标链、Goerli、Sepolia、Ropsten 等                  |
| [Prysm](https://docs.prylabs.network/docs/getting-started/)  | Go         | Linux、Windows、macOS | 信标链、Gnosis、Goerli、Pyrmont、Sepolia、Ropsten 等 |
| [Teku](https://consensys.net/knowledge-base/ethereum-2/teku/) | Java       | Linux、Windows、macOS | 信标链、Gnosis、Goerli、Sepolia、Ropsten 等          |
| [Grandine](https://docs.grandine.io/)                        | Rust语言   | Linux、Windows、macOS | 信标链、Goerli、Sepolia 等                           |

##### 同步模式

同步方法如下：从对等节点下载数据，用加密方法验证其完整性，并构建一个本地区块链数据库。

客户端在实现同步算法方面也各不相同。 有关实现的具体细节，请参考你所选客户端的官方文档。

##### 执行层的同步

分为完全同步，快速同步，快照同步，轻量同步

###### 完全同步

完全同步会下载所有区块（包括区块头和区块体），并通过执行自创世块以来的每个区块，以增量方式重新生成区块链的状态。

[存档节点](https://ethereum.org/zh/developers/docs/nodes-and-clients/#archive-node)会执行完全同步，以构建（并保留）每个区块中每笔事务所做的状态更改的完整历史记录。

###### 快速同步

与完全同步一样，快速同步会下载所有区块（包括区块头、交易和收据）。 不过，快速同步并不重新处理历史交易，而是依赖收据，直至到达最近的头部时，再切换到导入和处理区块，以提供一个完整的节点。（可以减少带快使用）

###### 快照同步

逐块验证链。不是从创世区块开始，而是从一个最近的已知为真实区块链一部分的受信任检查点开始。节点会定期保存检查点，同时删除早于某个时间的数据。 这些快照被用于在需要时重新生成状态数据，而不是永久储存它。

- 最快的同步策略，目前是以太坊主网的默认策略。
- 节省大量磁盘空间和网络带宽，同时不牺牲安全性。

###### 轻量同步

轻客户端模式下载所有区块头和区块数据，并对其中一些进行随机验证。 仅从可信的检查点同步链的头部。

- 仅获取最新状态，同时依赖于对开发者和共识机制的信任。
- 客户端在几分钟内便可以使用当前网络状态。

##### 共识层的同步

###### 乐观同步

是合并后同步策略，允许执行节点通过已确立的方法进行同步。执行引擎可以在不进行完全验证的情况下*乐观地*导入信标区块，找到最新区块头，然后使用上述方法开始同步链。 接着，在执行客户端更新之后，它将通知共识客户端信标链中交易的有效性。

**先导入，再确认**

###### 检查点同步

也叫弱主观性同步，从最近的弱主观性检查点而不是从创世块同步信标链。检查点同步可大幅加快初始同步速度，其信任假设与从创世块同步时类似。

在实践中，这意味着你的节点会连接到远程服务，以下载最近的最终确定状态并从该点继续验证数据。 提供数据的第三方会受到信任，因此要谨慎选择。
### 2025.02.08

#### Study Group 2024 week2 学习

#### 学习内容

观看thereum Execution Layer Overview | lightclient视频

#### 概念补充

##### gas

as 是衡量交易和智能合约执行时所消耗计算资源的单位，其消耗量决定了需支付的交易费用，同时通过限制资源消耗来防止网络滥用。

Gas 的使用量主要取决于交易或合约调用中执行的操作类型和复杂性，交易中操作越简单、状态变化越少、计算越轻量，gas 使用就越少；而操作越复杂、需要修改状态或执行大量计算时，则会消耗更多 gas。

##### Deneb Beacon Chain

以太坊共识层——即Beacon Chain，在经过“Deneb”升级后所呈现的新版形态。简单来说：

- **Beacon Chain 的作用**：Beacon Chain 是以太坊采用权益证明（PoS）共识机制的核心链，负责管理验证者、组织区块生产和确认，以及协调网络安全。
- **Deneb 升级**：Deneb 是以太坊后续升级计划中的一个阶段（常与Capella等升级配合），旨在改善Beacon Chain的性能和数据处理能力，提升网络效率，并为未来扩容（如Danksharding）做准备。

因此，“Deneb Beacon Chain”就是指在完成Deneb升级之后的Beacon Chain版本，它通过一系列技术改进，提高了共识效率、数据可用性和整体网络扩展性。

#### 视频主要内容

##### 1 执行层的区块验证

执行层现在更像是一个状态转换函数

```go
// 接收父区块、当前区块和当前状态（StateDB）作为参数。
// 首先调用 core.VerifyHeaders 验证区块头（确保区块头信息符合规定，如时间戳、难度、父区块哈希等）。
// 然后遍历区块中所有交易，对于每笔交易调用 vm.Run 在虚拟机中执行，更新状态。
// 如果在验证区块头或执行某笔交易时出错，则立即返回错误，说明该区块无效；如果所有操作都成功，则返回更新后的状态。
func stf(parent types.Block, block types.Block, state state.StateDB) (state.StateDB, error) {
    if err := core.VerifyHeaders(parent, block); err != nil {
        // header error detected
        return nil, err
    }
    for _,tx := range block.Transactions() {
        res, err := vm.Run(block.Header(), tx, state)
        if err != nil {
            // trasaction invalid, block is invalid
            return nil, err
        }
        state = res
    }
    return state, nil
}
// 这个函数调用了 stf函数来处理（执行）一个执行载荷（ExecutionPayload）。
// 如果执行过程中没有错误，说明载荷中的交易都合法，则返回 true；否则返回 false，表示载荷无效。
func newPayLoad(execPayload engine.ExecutionPayload) bool {
    if _, err := stf(..); err != nil {
        return false
    } 
    return true
}
```

- 合并后，执行层（Execution Layer）的职责简化，主要负责状态转换功能（State Transition Function）。
- 共识层（Consensus Layer）接管了区块排序、重组（reorgs）等任务，执行层仅需验证区块的有效性并生成新的状态。
- 执行层通过 `process_execution_payload` 函数与共识层交互，返回区块是否有效的布尔值。
- 验证区块头（Header）的合法性，包括父哈希、时间戳、Gas Limit（需符合1/1024调整规则）、Base Fee计算等。
- 执行层调用 `state_transition` 函数，逐笔执行交易并更新状态数据库（State DB）。
- 若交易执行失败（如Gas不足或无效Nonce），整个区块会被标记为无效。

##### 2 区块构建

```go
func build(env Environment, pool txpool.Pool, state state.StateDB) (types.Block, state.StateDB, error){
    var (
    	gasUsed = 0 // 定义一个变量 gasUsed，初始值为 0，用来累计已消耗的 Gas。
        txs []types.Transactions // 定义一个交易列表 txs，用于存放从交易池中挑选并执行成功的交易。
    )
    // 循环条件是“当已消耗的 gas 小于环境设置的 GasLimit 或者交易池非空时”（注意：这里的条件写成“||”，即只要有一个条件满足就继续循环）。
    for ; gasUsed < env.GasLimit || ! pool.Empty(); {
        tx := pool.Pop() // 在每次循环中，从交易池中弹出一笔交易（tx := pool.Pop()）。
        // 调用 vm.Run(env, tx, state) 在虚拟机中执行这笔交易。该函数返回三个值：
        // res：执行后的新状态；
        // gas：该笔交易实际消耗的 gas 数量；
        // err：执行过程中产生的错误（如果交易无效，则返回错误）。
        // 如果执行过程中出错（例如交易无效），则跳过这笔交易（continue），不把它加入区块中。
        res, gas, err := vm.Run(env, tx, state)
        if err != nil {
            // tx invalid
            continue
        }
        // 如果交易执行成功，则将该交易消耗的 gas 累加到 gasUsed 上。
        // 将这笔交易添加到交易列表 txs 中。
        // 更新状态 state 为这笔交易执行后的结果 res。
        gasUsed += gas
        txs = append(txs, tx)
        state = res
    }
    // 循环结束后，调用 core.Finalize(env, txs, state) 对交易列表和状态进行最终处理，生成一个完整的区块，并返回该区块、最终状态和可能的错误。
    return core.Finalize(env, txs, state)
}
```

- 交易池（Transaction Pool）按Gas价格排序交易，优先选择高Gas费的交易填充区块。
- 通过循环执行交易，累积Gas使用量，直到达到区块Gas上限（如30M）。
- 最终调用 `Finalize` 函数生成完整的区块，包含交易哈希、收据哈希等默克尔根。

##### 3 状态转换函数

代码见go-ethereum

- 状态转换函数的核心是逐笔执行交易，通过EVM（以太坊虚拟机）更新状态。
- EVM执行时需传入区块上下文（如Coinbase、时间戳）和交易上下文（如Gas Price）。
- 交易执行失败（如合约回滚）仅消耗Gas，不影响区块有效性，但无效交易会导致区块被拒绝。

##### 4 EVM工作原理与指令示例

- EVM是基于栈的虚拟机，指令包括算术运算（ADD）、存储操作（SSTORE）、环境指令（COINBASE）等。
- 示例：通过 `MSTORE` 将数据写入内存，`RETURN` 返回结果。
- 每个EVM调用帧（Call Frame）包含独立的栈、内存和Gas计数器。

##### 5 点对点（P2P）协议与数据同步

- DevP2P协议负责广播交易、同步区块头和状态数据（通过 `eth/68` 和 `snap` 协议）。
- 交易广播采用“平方根广播”策略，减少带宽消耗。
- Snap Sync分两阶段：连续状态下载（Contiguous Retrieval）和状态修复（Healing），依赖默克尔证明验证数据完整性。

### 2025.02.09

#### Study Group 2024 week3 学习

#### 学习内容

观看Ethereum Consensus Layer | Alex Stokes | Week 3视频

#### 视频主要内容

##### 1 区块链与数字稀缺性

- 区块链的核心价值是创造“数字稀缺性”，解决数字世界中无法复制的资源问题（如货币、数字资产）。
- 传统中心化系统的缺陷：依赖单一信任方，易受攻击或操纵。
- 分布式共识的目标：通过多节点协作实现去信任化，确保协议规则自动执行。

##### 2 拜占庭容错（BFT）与共识机制

- 拜占庭容错（BFT）是分布式系统的核心问题，需保证即使部分节点故障或作恶，系统仍能达成一致。
- 传统BFT协议（如PBFT）的局限性：节点数量受限，消息复杂度高。
- 比特币的PoW创新：通过工作量证明实现开放网络的共识，但存在能源浪费和激励机制单一的问题。

##### 3 以太坊的权益证明（PoS）机制

- **PoS的核心设计**：验证者需质押32 ETH参与共识，通过经济惩罚（Slashing）增强安全性。
- **Slot与Epoch**：
  - Slot：12秒为一个时间单元，每个Slot由随机选出的验证者提议区块。
  - Epoch：32个Slot（约6.4分钟），用于批量处理验证者奖惩、状态更新等。
- **随机性（RANDAO）**：通过链上随机数生成验证者分配，确保公平性。

##### 4 以太坊共识协议（Gasper）

- **Gasper协议**：结合FFG（Friendly Finality Gadget）和LMD GHOST算法，实现动态可用性与最终性。
- **最终性（Finality）**：需2/3验证者投票确认的区块不可逆转，防止分叉。
- **分片与动态委员会**：通过随机分片降低单个验证者的负载，提升网络吞吐量。

##### 5 未来改进方向

- **单槽最终性（SSF）**：缩短最终性确认时间至单个Slot（12秒），减少攻击窗口。
- **提议者-构建者分离（PBS）**：分离区块提议与构建角色，降低MEV（最大可提取价值）对去中心化的影响。
- **验证者优化**：探索更高质押门槛（如2048 ETH）以减少节点数量，提升效率。

<!-- Content_END -->
