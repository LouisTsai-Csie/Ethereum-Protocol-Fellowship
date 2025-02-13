---
timezone: Pacific/Auckland
---

# Bruce Xu

1. 自我介绍：大家好，我是 Bruce Xu，以太坊爱好者，LXDAO 和 ETHPanda 联合发起人，很开心参加今年的 EPF 残酷共学。
2. 你认为你会完成本次残酷学习吗？会的！

## Notes

<!-- Content_START -->

# 2025.02.06

今天先把 https://epf.wiki/#/ 大概得过一下，看看整体结构和一些相关的信息，列一些 TODO 记录自己感兴趣的话题和内容，进行下一步的学习。

填写了 survey：<https://forms.gle/G5V95qyGV8uMjKGcA>

今年的 EPFsg 是 2 周 intense 的之前课程回顾，然后 6 周新的在线课程，覆盖几个部分。

TODO 这两周可以快速复习 https://epf.wiki/#/eps/SG2024 24 年的课程和笔记。


## [Prehistory of Ethereum](https://epf.wiki/#/wiki/protocol/prehistory)

以太坊的愿景来自于互联网早期的开放精神、Unix、GNU/Linux、Cypherpunks、比特币等等，构建一个无边界、自我主权的数字经济生态。

"National borders are just speed bumps on the information superhighway."
— Timothy May, Cypherpunk.

互联网的兴起，打破了国家的便捷，促进了不可想象的人类互动。

密码学和开源软件作为根基，促进了互联网新人，助推了电子商务和网上银行业务的增长。

Free software 的 free 是 freedom 而不是 price。但是 FOSS 是非常有价值和贡献的。

90 年代开始，密码朋克就有很多次对于实现 digital currency 的尝试，例如 Digicash、E-Gold、B-Money、Bitgold、Bitcoin。而 Bitcoin 上面开发应用程序的几次尝试都失败了，所以有了 Ethereum 的诞生。

分享：<https://x.com/brucexu_eth/status/1887257222436298803>

## [Protocol Architecture Overview](https://epf.wiki/#/wiki/protocol/architecture)

执行层处理实际交易和用户交互，共识层提供证明的共识机制。

## [Protocol Design Philosophy](https://epf.wiki/#/wiki/protocol/design-rationale)

- 简单
- 普遍：图灵完备的虚拟机
- 模块化
- 中立不歧视
- 敏捷

原则：

- 尽量简单
- Freedom：使用时，不会受到限制或者歧视。
- Generalization
- 没有任何特性：可以通过智能合约自己设计

实际上我感觉以太坊协议还是太复杂了，避免不了软件工程的屎山的归途。按照架构的演进，模块化肯定是必然，分层的设计需要非常清晰和能看到全局的资深研究员。

TODO 绘制以太坊的分层架构图。

UTXO vs Account：这是个比较大的话题，不过智能合约的实现，账号确实是比较好的选择。

Merkle-Patricia Trie 是以太坊的存储数据结构，高效检索的能力构成了以太坊状态的各项数据。

TODO 获取一下以太坊的 state tree 真实数据看看

MPT 正在被考虑弃用，准备使用 Verkle tree，实现更高效的数据结构。

TODO 简单了解 MPT 之后，重点研究 Verkle tree

目前的节点状态数据包括 1-2TB，其实挺麻烦的，启动节点等还是比较麻烦的。

# 2025.02.07

## [Protocol Design Philosophy](https://epf.wiki/#/wiki/protocol/design-rationale)

Recursive Length Prefix (RLP) 创建新序列化方案的理由在于其他方案的概率性质。RLP 通过简单而确定的序列化解决了这一问题，并保证了绝对的字节级一致性。这是一个序列化数据的算法？

Simple serialize (SSZ) 序列化是将数据结构转换为可以传输并在以后重建的格式的过程。SSZ 是以太坊 2.0 信标链中使用的一种序列化格式。根据 Vitalik 的评论，SSZ 试图解决的一个主要问题是 RLP 不允许 Merkle 化，这将意味着排除了任何简洁轻客户端证明的可能性。因此，无法实现无状态性——而无状态性仍然是当前以太坊研发的关键目标。

Casper Friendly Finality Gadget (FFG) 用于实现 finality，finality 表示的是一个 block 和里面的数据，再也无法被修改或者 remove。通过在 proposal 机制之上，通过选择代表 canonical transaction ledger 的唯一链来最终确定区块。

Byzantine Fault Tolerance (BFT) 拜占庭将军容错是一个分布式计算系统的特性。应对的挑战是在一个去中心化的环境，如何在某些节点故障或者存在恶意行为下达成一致。比如 PoS 就是针对这个问题实现的算法，来确保在去中心化环境下实现一致。

Latest Message Driven Greediest Heaviest Observed Sub-Tree (LMD-GHOST) 是一个分支选择的规则。有点类似 PoW 使用的分叉选择，其中完成最多工作的被选为 canonical chain。

Gasper 是一个完全的 PoS protocl，结合了 casper FFG 和 LMD-GHOST 来推动 Eth2 的共识层机制。

Using a DHT DHT（分布式哈希表）的主要优势在于，它的查找操作在网络中仅产生对数级别的通信开销。因此，它非常适用于在 P2P 网络中查找（查询）内容。但一个直接的问题是：在以太坊中，我们为什么需要查找内容？毕竟，大多数节点都关注相同的内容——即最新的区块。由于共识槽（consensus slot）在每个时刻只会产生一个区块，并且该区块通过gossip 协议进行传播，因此链的最新状态（tip of the chain）始终是一致的。在 BitTorrent 和 IPFS 这样的协议中，DHT 用于存储各种内容，并帮助用户查找他们感兴趣的内容。而在以太坊的网络层，DHT 并不是用于查找区块，而是用于发现不同的对等节点（peers）。

discv5 是一个 Ethereum 使用的 discovery protocol，使用 kademlia based DHT 来存储 ENR records. ENR 记录包括路由信息来建立 P2P 链接。

# 2025.02.08

## [Protocol history and evolution](https://epf.wiki/#/wiki/protocol/history)

几个比较重要的以太坊升级：

- Frontier 是 Ethereum Protocol 的发起，在 2015 7 月 30 日上线，创世区块 <https://etherscan.io/block/0>
- Homestead 在 2016 年 3 月 14 日上线。是一个更加成熟稳定的平台，包括 EIP-2、EIP-7、EIP-8 等升级
- The Merge 在 2022 年 9 月 15 日上线，将共识层机制切换为 PoS。然后 PoS 共识层分开放在了一个新的 Beacon Chain Layer，有自己的 p2p 网络和逻辑。Beacon Chain 从 2020 年 12 月 1 号就开始运行和测试，没有发现什么问题。

# 2025.02.09

开始学习去年 EPFsg 的资料：https://epf.wiki/#/eps/week0

## Week0

[Merkle Tress](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)

所有以太坊目前的数据包括 all accounts、balances 和 smart contracts（？合约是怎么用 Merkle Tree 存储的）使用了 Merkle Tree 进行编码。主要好处是一个 root value 可以用于验证数据。

以太坊数据结构是 modified Merkle-Patricia Trie，使用了 PATRICIA 来实现高效数据读取。“Patricia”部分主要是为了减少节点高度、节省存储空间，将重复前缀合并到同一个路径上。

Merkle Tree 是不包含数据的，而是对数据进行 hash 然后链接起来成为一棵树，然后通过提交从叶子节点到根节点的一条 hash 路径来生成或者验证一个数据是否存在或者被篡改。

在以太坊中，用 MPT 来保存“世界状态（全局账户的余额、合约存储等）”。每次状态更新都会导致相应的 MPT 变化，从而生成一个新的根哈希（state root）。

trie 是一种类型的 tree，包括 prefix tree 等，带有一些特殊逻辑的 tree。

# 2025.02.10

对于 radix tree 而言，通过 root hash 的存储查询，是会通过 key-value 的方式，将序列化节点数据存储到了某个地方，这样可以查出来整个树。拿到的节点数据反序列化，例如 Ethereum 的 RLP，然后可以拿到根节点对应的完整结构，包括子节点、前缀信息等。然后继续递归调用查询子节点数据，直到目标的叶子节点。感觉如果树的层级太深会比较麻烦，所以尽量扁平，然后每个树叶子节点也不要太多。

```
   def update(node_hash, path, value):
        curnode = db.get(node_hash) if node_hash else [ NULL ] * 17
        newnode = curnode.copy()
        if path == '':
            newnode[-1] = value
        else:
            newindex = update(curnode[path[0]], path[1:], value)
            newnode[path[0]] = newindex
        db.put(hash(newnode), newnode)
        return hash(newnode)
```

更新 radix 树的操作，就是递归调用遍历 `[i_0, i_1 ... i_n, value]` 这个结构，然后对最后的一个 value 进行更新，同时返回将整个链路的 hash index 更新。

MPT

Radix tries 不够高效，比如 Ethereum EOA 64 characters 长度的地址，每次 lookup 或者 delete 都需要 64 steps。所以 Patricia Trie 引用了下面的办法来解决问题：

A node in a Merkle Patricia trie is one of the following:

- NULL (represented as the empty string)
- branch A 17-item node [ v0 ... v15, vt ]
- leaf A 2-item node [ encodedPath, value ]
- extension A 2-item node [ encodedPath, key ]

由于地址比较长，所以中间或者某段结构，可能并不需要挨个字符进行下降，所以通过 encodedPath 进行存储路径快速下降。

Tries in Ethereum

State Trie

There is one global state trie, and it is updated every time a client processes a block. 路径是 keccak256(ethereumAddress) 然后值是 rlp(ethereumAccount)。具体一点 account 是 `[nonce,balance,storageRoot,codeHash]` 这四个 item。

Storage Trie

Storage trie is where all contract data lives. There is a separate storage trie for each account.

Transactions Trie

路径是 rlp(transactionIndex)。There is a separate transactions trie for every block, again storing (key, value) pairs.

Receipts Trie

Every block has its own Receipts trie. A path here is: rlp(transactionIndex).

TODO 提取一下上面这些 Trie 的原始数据结构，进行解码看看。

# 2025.02.11

## https://medium.com/coinmonks/ethereum-data-transaction-trie-simplified-795483ff3929

![image](https://github.com/user-attachments/assets/1cf70c09-1a4a-48d7-b2c8-52e751b38c89)

Light clients are nodes that do not contain entire blockchain data. Instead, they download only the chain of block headers. They cannot take part in block validation however they can access the blockchain in a similar way as the full node does.

![image](https://github.com/user-attachments/assets/2ccae255-5dfd-4268-a2a3-4de3e51c7898)

轻客户端通过读取对应 block 的 txs 然后自己计算 hashes 来对比 root hash 是不是一样的。通过 merkle tree 来实现的话，然后并不需要全部的 tx 就可以，只需要选择几个就可以了。

![image](https://github.com/user-attachments/assets/3c001a97-fe90-47f5-a39c-b6070cea17dd)

选择要验证的 tx 的相关 hash 即可，因为上层的 hash 节点都是计算生成的。

TODO 跑一下代码 https://github.com/dajuguan/lab/blob/main/eth/randao.py

# 2025.02.12

## https://epf.wiki/#/eps/week1

![image](https://github.com/user-attachments/assets/3635c3a4-c051-4557-a8cb-0621a5b84467)

The Merge 的过程，其实是构建了一个平行的 Beacon Chain 一直在运行和检测，之后把 execution layer 接过来。

As hinted above, the main high level components of Ethereum are execution and consensus layer. These are 2 networks which are connected and dependent on each other. Execution layer provides the execution engine, handles user transaction and all state (address, contract data) while consensus implements the proof-of-stake mechanism ensuring security and fault tolerance.

The traditional development cycle for new features or changes is Idea - Research - Development - Testing - Adoption. However, problems might arise at any moment of this cycle resulting in iterating again from the beginning.

The coordination mainly happens via regular calls which are scheduled in the PM repo.

The ideas and proposed changes from the community are coordinated using EIP process. Additionally, there are a few discussion forums. The biggest one discussing core upgrades is https://ethresear.ch. Another forum which is connected to the EIP process and serves for discussion about specific proposals is Ethereum Magicians. Lots of important discussion is also happening on the R&D Discord server (ping us in EPFsg discord to get an invite) and in client team groups. There are also offsites or workshops where many core developers meet in person to speed up the process face to face.

通过 https://github.com/ethereum/pm 学习到的社区协调和管理经验：

1. 通过创建 issues + tag 来放议题、会议链接等信息，例如 https://github.com/ethereum/pm/issues/1253 包括全部的会议，不仅仅是 ACDE ACDC
2. 提供了一个 Google Calendar 来快速添加，但是目前不知道是自动还是人工维护的
3. 欢迎大家通过评论的方式，添加议题等
4. 写清楚了议题如何添加、谁能参加、谁主持等
5. ECH 提供了字幕稿，然后下面有个大表单，可以看到每次会议的录屏、notes、讨论等等

对 LXDAO 的启发：

- 可以考虑将会议集中在这里管理，避免在论坛占用大家的注意力
- 提供会议的速记和内容稿，作为社区周报的内容，而非比较制式的，重点在于引导大家讨论

TODO https://notes.ethereum.org/@mikeneuder/rcr2vmsvftv

# 2025.02.13

## https://epf.wiki/#/eps/week2

### https://github.com/ethereum/consensus-specs/blob/dev/specs/deneb/beacon-chain.md#modified-process_execution_payload

```
class ExecutionPayload(Container):
    # Execution block header fields
    parent_hash: Hash32 # 上一个区块的 hash，连起来
    fee_recipient: ExecutionAddress  # 'beneficiary' in the yellow paper 执行层中，是区块提交者的地址
    state_root: Bytes32
    receipts_root: Bytes32
    logs_bloom: ByteVector[BYTES_PER_LOGS_BLOOM] # 用于日志过滤的 bloom 过滤器，用于快速查找日志
    prev_randao: Bytes32  # 'difficulty' in the yellow paper
    block_number: uint64  # 'number' in the yellow paper
    gas_limit: uint64
    gas_used: uint64
    timestamp: uint64
    extra_data: ByteList[MAX_EXTRA_DATA_BYTES]
    base_fee_per_gas: uint256
    # Extra payload fields
    block_hash: Hash32  # Hash of execution block
    transactions: List[Transaction, MAX_TRANSACTIONS_PER_PAYLOAD]
    withdrawals: List[Withdrawal, MAX_WITHDRAWALS_PER_PAYLOAD] # 目前区块的提款列表
    blob_gas_used: uint64  # [New in Deneb:EIP4844]
    excess_blob_gas: uint64  # [New in Deneb:EIP4844]
```

需要进行能力扩展和数据增加，就是通过类似 EIP4844 这样的标准，创建新的标准，然后客户端来实现读取和保存记录。

真实的信息和数据：

![image](https://github.com/user-attachments/assets/185dcd23-b49a-4980-8c9a-f6f66d365543)

![image](https://github.com/user-attachments/assets/51da5284-ff7a-44af-8b53-b286f9e35555)

![image](https://github.com/user-attachments/assets/7861ddc2-dc22-4da3-84aa-406d639f2eda)

logs_bloom 的工作原理：

- logs_bloom 是一个固定大小的位数组，通常为256字节，即2048位。
- 当一个新的日志被添加到区块中时，计算该日志的哈希值，并使用多个哈希函数（如3个）生成多个哈希值。
- 将这些哈希值映射到logs_bloom的位数组中，将对应的位设置为1。
- 查询某个日志是否存在于某个区块的时候，只需要计算日志的 hash，然后快速检查 logs_bloom 的对应的位置是否全部为 1，如果是，那么日志可能在当前区块。可能会存在误报
- 通过这个，可以快速过滤不包含特定日志的区块，提高检索效率，比如查询 event 发生在哪些区块，从而仅仅加载和处理相关区块

TODO Hackerscan 可以加入查看原始区块信息的功能，没有找到 logs_bloom 的原始数据

TODO Contract Internal Transactions 是什么？跟 Block 的 transactions 区别是什么？

TODO 明天把整个区块的所有信息和内容过一下 https://etherscan.io/block/21833528 https://eth.blockscout.com/block/21833528?tab=index

TODO randao
TODO withdrawals 提款工作原理？







<!-- Content_END -->
