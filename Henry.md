---
timezone: Asia/Shanghai
---

# Henry

1. 自我介绍
    大家好，我是 Henry，区块链技术爱好者，目前在进行系统安全相关的研究工作。
2. 你认为你会完成本次残酷学习吗？
    - Do for it!

## Notes

<!-- Content_START -->

### 2025.02.06

今日任务：
- [x] 学习以太坊（Ethereum）基础知识与背景->https://epf.wiki/#/eps/week1
- [x] 了解 EPF 相关的学习模式，做好学习规划

#### EL Client
了解了一下目前 ethereum 所使用的几种不同的执行层客户端。
它是由不同的团队使用不同的编程语言开发。这使得网络更加强大和多样化。理想目标是实现多样性，而没有任何客户端占主导地位，以减少任何单点故障。
主要包括以下五种，并且查看了目前主网的使用情况：Geth(53.56%)、Nethermind(29.58%)、erigon(6.52%)、besu(5.54%)、reth(4.57%)，另外有 EthereumJS 应该是 beta 测试中。

#### CL Client
从以太坊2.0后转向了 pos 共识，需要有共识层客户端和执行层客户端软件一起才能够构成一个完整的以太坊节点。共识层客户端主要负责所有与共识相关的逻辑，包括分叉选择算法、处理证明以及管理权益证明奖励和惩罚。目前主要包括：	
    •	Prysm：由 Prysmatic Labs 开发，使用 Go 语言编写。
	•	Lighthouse：由 Sigma Prime 开发，使用 Rust 语言编写。
	•	Teku：由 ConsenSys 开发，使用 Java 语言编写。
	•	Nimbus：由 Status 开发，使用 Nim 语言编写。
	•	Lodestar：由 ChainSafe 开发，使用 TypeScript 语言编写。
这些客户端由不同的团队使用多种编程语言开发，体现了以太坊网络的多样性和去中心化特性。客户端多样性增强了网络的安全性和稳健性，确保在面对潜在漏洞或攻击时，网络能够迅速恢复并保持正常运行。
此外，客户端多样性使网络在面对攻击和漏洞时恢复能力更强。多种客户端是以太坊独有的优势，而其他区块链依赖于单一客户端的无误性。

#### 小结
以太坊是一种公共区块链技术，主要由执行层客户端和共识层客户端构成。
执行层主要负责基础的节点执行逻辑（包括pow共识），共识层则只负责pos共识相关的业务。

### 2025.02.07
学习 geth 部分代码，浏览节点搭建文档

### 2025.02.08
继续学习 geth 源码。
1. 下载 geth 项目
> git clone https://github.com/ethereum/go-ethereum.git
2. 编译 geth cli  可执行文件 （位于 build/bin 目录下）
> make geth
3. 将可执行文件添加到环境变量中
> cp /build/bin/geth /usr/local/bin
4. 测试
> geth —help
1. 配置初始状态

要运行以太坊私有链，需要定义自己的创世区块，创世区块信息写在一个 JSON 格式的配置文件中。首先将下面的内容保存到一个 JSON 文件中，例如 `genesis.json`
```markdown
"config": {
        "chainId": 10, 
        "homesteadBlock": 0,
        "eip150Block": 0,
        "eip155Block": 0
    },
  "alloc"      : {},
  "coinbase"   : "0x0000000000000000000000000000000000000000",
  "difficulty" : "0x20000",
  "extraData"  : "",
  "gasLimit"   : "0x2fefd8",
  "nonce"      : "0x0000000000000042",
  "mixhash"    : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp"  : "0x00"
}
```

其中，chainID 指定了独立的区块链网络 ID。网络 ID 在连接到其他节点的时候会用到，以太坊公网的网络 ID 是 1，为了不与公有链网络冲突，运行私有链节点的时候要指定自己的网络 ID。不同 ID 网络的节点无法相互连接。配置文件还对当前挖矿难度 difficulty、区块 Gas 消耗限制 gasLimit 等参数进行了设置。

### 2025.02.09


<!-- Content_END -->
