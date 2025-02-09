---
timezone: Asia/Shanghai
---


# ThalesLiu

1. 我是ThalesLiu, solidity练习生，以太坊支持者
2. 你认为你会完成本次残酷学习吗？ 应该可以


## Notes

<!-- Content_START -->

### 2025.02.06

目前协议由 2 个主要部分组成 - 执行层和共识层。执行层 （EL） 处理实际交易和用户交互，是全球计算机执行其程序的地方。共识层 （CL） 提供权益证明共识机制 - 一种加密经济安全，确保所有节点都遵循相同的提示并驱动执行层的规范链。 目前以太坊协议面向未来采用了模块化，模块化源于封装复杂性的理念。当系统由子系统组成时，就会出现封装复杂性 —— 这些子系统内部很复杂，可以通过高级接口提供给外部。现在，这在子系统的选择和更好的单个组件调试方面产生了很大的灵活性。

### 2025.02.07
了解了一下目前 ethereum 所使用的几种不同的执行层客户端。 这使得网络更加强大和多样化。理想目标是实现多样性，而没有任何客户端占主导地位，以减少任何单点故障。 主要包括以下五种
##### 执行客户端
| 客户端                                                       | 语言       | 操作系统              | 
| ------------------------------------------------------------ | ---------- | --------------------- | 
| [Geth](https://geth.ethereum.org/)                           | Go         | Linux、Windows、macOS | 
| [Nethermind](https://www.nethermind.io/)                     | C#、.NET   | Linux、Windows、macOS | 
| [Besu](https://besu.hyperledger.org/en/stable/)              | Java       | Linux、Windows、macOS | 
| [Erigon](https://github.com/ledgerwatch/erigon)              | Go         | Linux、Windows、macOS | 
| [Reth](https://reth.rs/)                                     | Rust       | Linux、Windows、macOS | 
| [EthereumJS](https://github.com/ethereumjs/ethereumjs-monorepo) | TypeScript | Linux、Windows、macOS | 

### 2025.02.08
以太坊权益证明的核心是一条称为“信标链”的系统链。信标链存储和管理验证者注册表。在权益证明的初始部署阶段，成为验证者的唯一机制是将 ETH 交易单向（Capella 后可提现）到以太坊工作量证明链上的存款合约。当信标链处理存款收据、达到激活余额并完成排队过程时，就会激活验证者。退出要么是自愿的，要么是作为对不当行为的惩罚而被迫进行的。信标链上的主要负载来源是 “证明”。证明同时是分片块的可用性投票（在以后的升级中）和信标块的权益证明投票（第 0 阶段）。

### 2025.02.09
EIP-4844，也称为 proto-danksharding，是 Deneb/Cancun 硬分叉的一部分。它为以太坊引入了数据可用性层，允许在区块链上临时存储任意数据。这种以这种方式存储的任意数据称为 blob，每个块可以有 3 ~ 6 个 blob sidecar（blob 的包装器）。EIP-4844 标志着以太坊迈向分片和可扩展性的第一步，使第 2 层解决方案 （L2） 能够使用此数据可用性层来降低 gas 费用并处理更多交易。

<!-- Content_END -->
