---
timezone: Asia/Bangkok
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)
---

# dixia

1. 自我介绍: 一名 Crypto 研究员
2. 你认为你会完成本次残酷学习吗？Try my best
3. TG 联系方式：@imkurt

## Notes

<!-- Content_START -->

### 2025.02.06

Node and EL. But is this a physical scope separation? Need to learn more. 

EOA controlled by key pair. Contract controlled by code.

Every smart contract's persistent storage is just an array of 32bytes. the root is a MPT hash. Does balance take up space of storage?

Message are just tx from contract without signature. but then how does other contracts know the message is from the initial contract?
And how does EVM or consensus verify the message(virt tx)?

https://cs251.stanford.edu/lectures/lecture7.pdf [0]

### 2025.02.07

Block Data Structure: world state root has MPT hash of all accounts on Ethereum.

It takes 16tb to run an archive node rn.

EVM still use stack (max: 1024) to execute code but with JUMP instruction code.

Burn ether preventing off-chain fee refund agreement to proposers that I did not thought before. A proposer could create/encourage fake txs to farm more ether reward if eth not burn and refund gas fee off-chain. The fee they paid would be less than eth reward to block proposer which it is the case given there are eth inflation for block proposers. But why would proposer are incentivized to do this? they could just collect reward from block building with the trouble of creating fake txs unless the block reward is proportional to the txs they included?

In bitcoin's world, miner has fixed cost for mining the block but they do get fee reward as well. So this could apply to Bitcoin as well

### 2025.02.08

#### Why would proposer engage into off-chain fee refund agreement

It is not due to the block reward as it is not proportional to the txs they included. But for the following reason:

1. Proposer could fake up transactions to create a impression/illusion of higher activity on the chain. Given if they could get the gas fee back the cost of artificially creating txs is very low (transaction fee + effort to inflate txs). But that would require you control majority of the validator nodes or can reliably predict the next block proposer. The former could be the case actually right now? given there are 2-3 block builder building most of the blocks.(builder == proposer?) 

2. To bid up the gas fee so other users have to pay more to get their txs included. This could require the same condition as above. As you intentionally pay a higher gas fee but can recover most of it back. It would be in the interest of proposer to do so. This would apply to Bitcoin as well. If majority of mining pool has an agreement. Could very well be the case for other chains.

#### 
gas fee right felt like a spam preventing mechanism rather than a fee market which pricing different resources.

encrypted mempool: total gas case has to be unencrypted. Cosmos has encrypted mempool. general idea is no complete solution available yet
<!-- Content_END -->
