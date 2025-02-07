---
timezone: Asia/Shanghai
---
---

# DylanYang

1. Dylanyang 经济学 工程双背景， 曾就职于腾讯，网易，阿里巴巴，是数据开发和后端开发，现就职于OKX DEX业务。技术栈为 java，go，rest。 热爱以太坊 
2. 会完成本次残酷共学

## Notes

<!-- Content_START -->

### 2025.02.06

无状态客户端是指无需存储整个状态数据库来验证传入区块的客户端。

https://blog.rachitasrivastava.com/verkle-tries-explained-a-simple-guide-for-beginners

https://www.youtube.com/watch?v=RGJOQHzg3UQ

https://dankradfeist.de/ethereum/2021/06/18/verkle-trie-for-eth1.html

https://blog.ethereum.org/2021/12/02/verkle-tree-structure

https://blog.rachitasrivastava.com/verkle-tries-explained-a-simple-guide-for-beginners

https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/ 

https://www.ccn.com/education/crypto/merkle-vs-verkle-trees-key-differences-explained/

验证区块链需要每个客户端存储头部区块和多个历史区块的整个状态三元组

- **存储多个历史区块的状态三元组**：
    - 每个区块的状态三元组包括：
        1. **状态树**：记录账户的余额、存储的智能合约代码及状态。（这个是最大的）
        2. **交易树**：记录区块中所有的交易列表。
        3. **收据树**：记录交易的执行结果（如 Gas 消耗、事件日志）。
    - 客户端需要这些数据来逐步回溯和验证区块链上的交易历史，以及验证交易执行是否正确。
- **为了验证每一个状态更新是否正确，客户端需要访问历史区块的状态三元组。**

https://vitalik.eth.limo/general/2021/06/18/verkle.html

https://ethereum.org/en/roadmap/verkle-trees/

https://verkle.info/

[https://notes.ethereum.org/@vbuterin/verkle_tree_eip#Illustratio](https://notes.ethereum.org/@vbuterin/verkle_tree_eip#Illustration)

https://vitalik.eth.limo/general/2024/10/26/futures5.html

**EIPs:  EIPs：**

- [**EIP-6800: Ethereum state using a unified verkle tree (draft)EIP-6800：使用统一verkle树的以太坊状态（草案）**](https://github.com/ethereum/EIPs/pull/6800)
- [**EIP-4762: Statelessness gas cost change (draft)EIP-4762：无国籍气体费用变化（草案）**](https://eips.ethereum.org/EIPS/eip-4762)
- [**EIP-7545: Verkle proof verification precompile (draft)EIP-7545：Verkle 证明验证预编译（草案）**](https://github.com/ethereum/EIPs/pull/7926)
- [**EIP-2935: Save historical block hashes in state (draft)EIP-2935：在状态中保存历史块哈希值（草案）**](https://eips.ethereum.org/EIPS/eip-2935)

Verkle 树和 Merkle Patricia 树在结构上的唯一真正区别是，Verkle 树在实践中更宽。宽得多。帕特里夏树在 `width = 2` 时效率最高（因此以太坊的六叉帕特里夏树实际上是相当次优的）。另一方面，Verkle 树的宽度越大，证明的时间就越短；

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/ccbfda19-7120-4f10-991d-ca3ef7646347/de1d5f0a-d9a3-43d6-966d-8a143a1dcfca/image.png)

Path Compression:  a) 路径压缩：

```jsx
Before:          After:
   A              A+B+C
  / \               |
 B   D              D
 |
 C

```

```jsx
Merkle Tree:                Verkle Trie:
     H                         VC
   /   \                    /  |  \
  H     H                 VC  VC  VC
 / \   / \               /|\  /|\  /|\
D   D D   D             D D D D D D D D

H = Hash
VC = Vector Commitment
D = Data

```

在MPT 中

要验证数据，不仅需要有连接每个叶子和根节点的所有中间哈希值，还需要有所有 "兄弟 "节点。证明中的每个节点都有一个同级节点，与之进行哈希运算后，就能创建出三元组上的下一个哈希值。这需要大量数据。

Verkle = 向量承诺 + 梅克尔。基本上是梅克尔树，但使用的是向量承诺而不是哈希值。

多项式承诺允许验证具有固定的大小，而不管它证明了多少叶。

使用的是向量承诺而不是哈希值。

### 2024.07.12

<!-- Content_END -->
