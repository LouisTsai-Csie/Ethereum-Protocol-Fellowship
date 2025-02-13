---
timezone: Asia/Shanghai
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# {你的名字}
YenChih Liao
1. 自我介绍
web3 developer, 朋友推坑第一次嘗試參加

2. 你认为你会完成本次残酷学习吗？
50/50

3. 你的 Telegram
@YenCLooo

## Notes

<!-- Content_START -->

### 2025.02.08
Finished week0 and week1

The week1 contains a lot of useful info, despite the vedio recording of somehow hard to focus on. The [quiz](https://ethereum.org/zh/quizzes/) is extremely helpful

Picked up/strengthened some key concepts
- Pretty Good Privacy (PGP) protocol, Signal protocol (both asymatric)
- Stacking offline panelty
- Proto-Danksharding and Danksharing
- validator --(Beacon APIs)-- Consensus layer --(Engine API)-- Execution layer --(JSON-RPC API)-- User/Web3

### 2025.02.09
Finished week2 Pre-readings

Picked up/strengthened some key concepts
- Patricia Merkle Tries
- Archival nodes (13TB in Feb. 2023)
- Front running attack awareness
- MSTORE/LOAD: 3gas, SSTORE: 20k, 5k, -15k

Further study:
- Transaction Fee Mechanism Design (About EIP1559)

### 2025.02.10
Finished week2

Picked up/strengthened some key concepts
- No more uncle blocks after the Merge
- The withdrawal functionality in the Beacon Chain allows stakers (validators) to receive their staking rewards (interest) automatically when blocks are finalized.
- p2p protocol broadcast tx to square root of peers
- snap sync protocol: contrast to full sync

### 2025.02.11
Finished week3

Picked up/strengthened some key concepts
- Each "slot" has a block unless a validator failed/missed to propose
- Every blocks have a bunch of "attestation"
- Attestations of a block are included into the next block
- Every 32 slots forms a "Epoch" (for mainnet)
- Slashes and rewards are evaluated at the end of every epoch
- The full validator set is randomly shuffled and distributed to one of slots in a epoch
- Each validator only verifies once in a epoch
- Justification: 2/3 of validators attested
- Finialize: Justifying a justified block

### 2025.02.12
Finished week4

It's talking about all the different ways/frameworks of testing. Without some concrete examples, it's really hard to get the merits of each of them

Picked up/strengthened some key concepts
- Execution Spec tests: Generate tests for EL clients
- Fuzzy Differential State Testing: Run a fuzzy smart contract and compares resulting state root of differenet clients
- Blockchain Testing: Similar to the previous test but on the scope of block hashes
- Hive Test: generate CL and EL for specific tests
- Shallow-fork: Early hard-fork from limited nodes

<!-- Content_END -->
