---
timezone: Asia/Shanghai
---

# {Devbards}

1. 自我介绍
  - Full Stack Engineer, starting to learn crypto and security-related topics to become a better developer.
2. 你认为你会完成本次残酷学习吗？
  - Sure!
3. TG 联系方式：@Devbards

## Notes

<!-- Content_START -->

### 2025.02.06

I had finished week 0 and week 1 study materials.
Like what Mario said, the first five weeks are about the introduction of Enthereum.
That is, I would be able to write some code after that.

-- one take away daily --
The Merkle Tree calculates the hash value by combining each node with its neighboring node to generate the parent node value.
This means that checking the final node value can be used to verify the entire tree.
Any change to a node will result in a different hash value, making it impossible to pass verification.
It is a fundamental mechanism in cryptocurrencies.

### 2025.02.07

Week 2 is about how Ethereum’s execution layer works. The Execution Layer (EL) processes transactions and keeps the network running smoothly. Every transaction goes through a validation process, gets executed, and then updates Ethereum’s state. There’s a lot happening under the hood, such as adjusting gas fees (EIP-1559) and handling staking withdrawals.

Ethereum nodes don’t just verify transactions—they also build new blocks by collecting transactions from the network. This requires a transaction pool to keep track of pending transactions before they’re added to a block. I wonder whether that causes latency or not.

The State Transition Function is responsible for processing blocks and updating Ethereum’s state. The Ethereum Virtual Machine (EVM) runs smart contract code using a stack-based system, meaning operations are processed one after another.

The P2) network plays a crucial role in how Ethereum nodes share data, whether it’s historical records, pending transactions, or state syncing (like with snap sync). To make everything accessible, Ethereum provides a JSON-RPC interface, allowing developers to interact with the blockchain using standard API calls. However, would this become a critical issue if the network were hacked?

### 2025.02.08
Week 3 covered consensus mechanisms, but to be honest, I didn’t fully grasp everything. So I’m reading it together with Week 4 to get a better understanding. However, there are still some parts that require further clarification. I plan to review everything again after going through Week 5.

<!-- Content_END -->
