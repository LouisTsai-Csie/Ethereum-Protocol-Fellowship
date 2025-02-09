---
timezone: Asia/Shanghai
---

---

# Bill

1. 自我介绍
Hi, my name is Bill. I'm  a security researcher focusing on the Ethereum ecosystem. 
2. 你认为你会完成本次残酷学习吗？
Yes.

## Notes

<!-- Content_START -->

### 2025.02.07
- [Verkle tree](https://app.tana.inc?nodeid=a2vr0fOui4HL) 
  - To replace [Merkle-Patricia trie](https://app.tana.inc?nodeid=j_Gd5E4ODZM0) because proofs consumes too much bandwidth.
  - Branching factor k
    - O(kn) construction time
    - O(log_k(n))
  - Trade-off between computational power and bandwidth.
  - Proof is called witness.
- To replace [Merkle-Patricia trie](https://app.tana.inc?nodeid=j_Gd5E4ODZM0) because proofs consumes too much bandwidth.
- Branching factor k
  - O(kn) construction time
  - O(log_k(n))
- O(kn) construction time
- O(log_k(n))
- Trade-off between computational power and bandwidth.
- Proof is called witness.
- [Recursive Length Prefix (RLP)](https://app.tana.inc?nodeid=aEyXev2UaVex) 
  - Other serialization schemes have a probabilistic nature.
  - Inefficient for fixed-length data types like bool and integers.
- Other serialization schemes have a probabilistic nature.
- Inefficient for fixed-length data types like bool and integers.

### 2025.02.09
- After discovering peers through [DHT](https://app.tana.inc?nodeid=EqOaJe-Z-ZPD) , peers use [gossip protocol](https://app.tana.inc?nodeid=ego5h76AG3BI) to disseminate the block throughout the network.
- To find different peers.
- Using a [DHT](https://app.tana.inc?nodeid=EqOaJe-Z-ZPD) 
  - To find different peers.
  - After discovering peers through [DHT](https://app.tana.inc?nodeid=EqOaJe-Z-ZPD) , peers use [gossip protocol](https://app.tana.inc?nodeid=ego5h76AG3BI) to disseminate the block throughout the network.
- Hunt for [Finality](https://app.tana.inc?nodeid=2UKh-XoVVM8r) 


<!-- Content_END -->
