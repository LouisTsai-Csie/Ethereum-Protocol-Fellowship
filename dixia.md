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

<!-- Content_END -->
