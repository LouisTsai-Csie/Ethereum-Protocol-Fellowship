---
timezone: Asia/Shanghai
---

# cooper

1. 自我介绍：大家好，我是 cooper， 区块链技术爱好者，Rust/Go开发工程师。很高兴参加 epf 残酷共学，希望通过这次学习，更详细的了解以太坊底层协议。
2. 你认为你会完成本次残酷学习吗？会的。

## Notes

<!-- Content_START -->

### 2025.02.06
> 周四

笔记内容

### 2025.02.07
> 周五

看了一下 https://epf.wiki/#/ 的目录。我希望在这次共学中重点学习的知识有以下几个，在wiki中没有包含的内容，我会从其他途径中尽量补充。

1）MPT 树的使用。如状态树、交易树。
2）当前以太坊的整体架构。
3）共识层、执行层机制。
4）EVM相关内容。

#### 相关事项
填写了 survey：<https://forms.gle/G5V95qyGV8uMjKGcA>

#### 学习内容总结
1）阅读了 [Prehistory of Ethereum](https://epf.wiki/#/wiki/protocol/prehistory) ，了解了以太坊的诞生背景。

2) 协议架构学习。
当前的协议架构是多年发展的结果。该协议由 2 个主要部分组成 - 执行层和共识层。执行层 （EL） 处理实际交易和用户交互，是全球计算机执行其程序的地方。共识层 （CL） 提供权益证明共识机制 - 一种加密经济安全，确保所有节点都遵循相同的提示并驱动执行层的规范链。

EL和CL的在各自的节点间，都维护着自己的P2P网络。EL和CL通过API进行交互。
![全局架构抽象图](https://epf.wiki/wiki/protocol/img/clients-overview.png)

![基础功能模块图](https://epf.wiki/wiki/protocol/img/protocol-overview.png)

3) 设计理念

- Simplicity
- Universality
- Modularity
- Non-discrimination
- Agility

4) 新的数据结构
文章提到，Merkle-Patricia trie被认为是可以弃用的。新的替代数据结构为：[Verkle tree](https://verkle.info/).

TODO: 值得仔细研究下。

> 以太坊的紧迫问题之一是当前的状态大小。估计约为 1-2TB（在撰写本文时）

5) Recursive Length Prefix (RLP)

RLP在我开发GDWeb3项目时已有详细了解。RLP是用于序列化以太坊交易和状态的编码格式。同时，大量的key-value数据存储时都使用了RLP规范进行数据的序列化。

GDWeb3项目中，集成了libethc的实现。代码参考：https://github.com/qingfengzxr/gdscript-web3/blob/main/modules/web3/ethprotocol/rlp.h

6）Simple serialize (SSZ)

SSZ 是以太坊 2.0 信标链中使用的一种序列化格式。设计为不是自描述的序列化方案，而是依赖于必须事先知道的架构。与 RLP 相比，SSZ 有很多优势，例如对象的高效重新哈希和快速索引，而 RLP 缺乏这些优势，因此复杂性很高。

SSZ 试图解决的主要问题之一是 RLP 不允许 Merkleization，这意味着取消任何简洁的轻量级客户端证明的可能性。因此，没有留下实现无状态的余地——而无状态仍然是当前以太坊研发的关键目标。

7）最终确定性

在以太坊基于权益证明的共识机制中，最终确定性是指保证在未销毁至少 33% 的 ETH 总质押量的情况下，无法更改或从区块链中删除区块。实现这一目标的底层共识协议称为 Casper Friendly Finality Gadget （FFG）。

Gasper 是完整的权益证明协议，是以太坊实现的理想化抽象。它结合了 Casper FFG 和 LMD-GHOST 来驱动 Eth2 的共识机制。

8）DHT

DHT 在以太坊网络中用于查找不同的对等节点，而不是区块。

以太坊网络层中的发现协议使用基于 kademlia 的 DHT discv5 来存储 ENR 记录。ENR 记录包含路由信息（互联网层的），用于在对等体之间建立连接。加入网络的对等节点使用引导节点在 DHT 中中继其node_id的查找查询。在此过程中，他们发现了其他对等体的 ENR 记录，这有助于他们填充路由表。通常，对等体还会随机查找 node_id来枚举网络，即找到所有对等体。

> 又接触到了新的知识点：ENR记录、kademlia based DHT、gossipsub。

以太坊网络中的区块使用 p2p 堆栈的 gossip 协议进行分发。通过底层 DHT 发现 Peer 节点后，Peer 节点使用覆盖网络 （gossipsub） 在整个网络中传播区块。覆盖网络使用路由信息创建自己的路由表，以建立连接和覆盖特定信息（订阅的主题、扇出等）这个覆盖网络确实是一个非结构化网络。

**以太坊的P2P实现协议为devp2p, 与 libp2p 的关系:**

libp2p项目与 devp2p 大约同时启动，旨在成为一组模块，用于通过模块化组件组装对等网络。关于 devp2p 和 libp2p 之间关系的问题经常出现。

很难比较这两个项目，因为它们的范围不同，并且在设计时考虑了不同的目标。devp2p 是一个集成系统定义，希望能够很好地满足以太坊的需求（尽管它也可能适合其他应用程序），而 libp2p 是一个编程库部分的集合，并不服务于任何特定的应用程序。

也就是说，这两个项目在精神上非常相似，并且 devp2p 在成熟过程中正在慢慢采用 libp2p 的部分功能。

**ENR记录(Ethereum Node Record):**

ENR 记录是节点在以太坊网络中进行通信的唯一标识。每个节点都有一个唯一的 ENR 记录，包含节点的网络地址、公钥、节点 ID 等信息。

以太坊节点记录最初是在EIP-778中提出的。



### 2025.02.08
> 周六

笔记内容

### 2025.02.09
> 周日

笔记内容

### 2025.02.10
> 周一

笔记内容

### 2025.02.11
> 周二

笔记内容

### 2025.02.12
> 周三

笔记内容

### 2025.02.13
> 周四

笔记内容

### 2025.02.14
> 周五

笔记内容

### 2025.02.15
> 周六

笔记内容

### 2025.02.16
> 周日

笔记内容


<!-- Content_END -->
