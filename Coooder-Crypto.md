---
timezone: Asia/Shanghai
---

# Coooder-Crypto

1. 自我介绍: 我是 Coooder，坚定的以太坊建设者哈哈哈
2. 你认为你会完成本次残酷学习吗？ 这次应该会了

## Notes

<!-- Content_START -->

### 2025.02.06

#### 今天做了什么：
1. 整体过了一遍 https://epf.wiki/
2. 制定了简单的计划
3. 学习了 Prehistory 部分
   
#### [Prehistory](https://epf.wiki/#/wiki/protocol/prehistory)
以太坊：无国界、主权自决的数字经济平台的愿景。

##### Prehistory 内容；
- 互联网与信息传输
- 加密需求
- 自由与开源遇到的阻力
- 密码朋克
- 比特币
- 以太坊

##### 加密朋克核心观点：
- 政府不应该能够窥探我们的事物
- 保护对话和交流是一项基本权利
- 权利通过技术而不是法律来保障
- 技术的力量会创造新的政治现实

#### 一些想法
虽然接触区块链有一段时间了，也很多次听说加密朋克，但是一直没有详细了解过相关的内容。这次竟然在 prehistory 的部分看到了相对完整的介绍，密码朋克的起源竟然这么早，感觉和自己想当然的理解完全不同。

今天看的 prehistory 部分，从互联网初期开始讲起，说 “In many ways, Ethereum functions like an open Bell Labs.”，感觉这些内容怪怪的，一方面我相信区块链技术的潜力，相信以太坊的未来，"like an open Bell labs" 实至名归；另一方面截至目前以太坊并没有掀起多么大的变革，这个说法让我这个通信工程专业的学生有点老脸一红。

不过都来学习以太坊协议了，当然是一直看好的，也会一直 build，希望早日看到新的突破。From "like an open Bell labs" to "beyond Bell labs"!


### 2025.02.07

#### 今天做了什么：
1. 继续看完了协议部分的架构、设计理由、演化

#### [协议架构](https://epf.wiki/#/wiki/protocol/architecture)

##### 两层：执行层（EL）和共识层（CL）
1. 执行层：处理实际交易和用户交互
2. 共识层：提供权益证明共识机制

#### [设计理念](https://epf.wiki/#/wiki/protocol/design-rationale)

##### 架构指导思想：
- 简单性：任何程序员在理想情况下都可以理解或实现整个规范，最大限度减少个人或者精英开发人员群体对协议的影响。
- 普遍性：以太坊没有功能，以太坊提供一个内部图灵完备虚拟机，称为 EVM。
- 模块化
- 非歧视性：协议本身不试图主动限制或者阻止特定类别的使用。
- 敏捷性：协议不是一成不变的。

##### 设计原则：
- 管理复杂性：
  - Sandwich model complexity：简化架构底层和以太坊接口，不可避免的复杂性放到协议的中间层。
  - Encapsulated complexity：优先级顺序：L2 > 客户端实现 > 协议规范
- 自由：使用以太坊协议的目的不受限制，-> 非歧视性
- 泛化
- 我们没有任何功能

##### 区块链协议
- Accounts over UTXOs（unspent transaction outputs）
  - 节省空间
  - 极大的可替代性
  - 简单性
- modified Merkle-Patricia Trie
- Verkle trees
- RLP 递归长度前缀
- SSZ 简单序列化

#### 一些想法
这部分难度有点大，有比较抽象的原则或许需要在后续的学习中慢慢理解。还有一些算法相关的内容，还没有完全搞懂，事已至此先睡觉吧，等后面再学～

<!-- Content_END -->
