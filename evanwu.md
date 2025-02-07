---
timezone: Asia/Shanghai
---

# {evan wu}

1. 自我介绍
大家好，我叫evan wu，从事web3开发有2年时间，希望和大家一起交流学习
2. 你认为你会完成本次残酷学习吗？
必须的
3. 你的 Telegram

## Notes

<!-- Content_START -->

### 2025.02.06
学习了以太坊的协议层架构，分为共识层(CL)和执行层(EL) 
其中：
CL：负责区块排序，提供共识证明，形成一个公共的账本
EL：负责和用户进行交易，以及交易的执行和交易状态的生产，是真正链上程序本地执行的地方

在具体实现中，CL和EL有各自独立的客户端，api以及p2p网络，CL和EL之间通过Engine api来进行交互，共同完成交易上链的过程

CL常见的客户端实现有：Prysm, Teku, Nimbus, Lighthouse, Lodestar
EL常见的客户端实现有：Besu，Erigon, Go-Ethereum(geth), Nethermind

### 2024.02.07
学习了以太坊账户模型的分类
以太坊账户模型可以分为EOA账户和Contract账户
EOA账户模型包含nonce和balance两个字段，balance用于记录账户余额，nonce从0开始递增，每发送一笔交易加1，这是为了防止交易重放
Contrac账户模型包含nonce、bance、storageRoot和codeHash四个字段，其中balance用于记录账户余额，nonce从1开始，通过该合约每部署一个新合约nonce值加1，storageRoot用于存放状态数据的roothash，而codeHash用于存放合约代码的hash值

对于EOA账户和Contract账户地址的生成：
EOA：hash(公钥）
Contract地址有create和create2两种生成方式
create：senderAddress + nonce
create2:keccak256(deployer_address ++ salt ++ keccak256(init_code))


### 2024.02.08

<!-- Content_END -->
