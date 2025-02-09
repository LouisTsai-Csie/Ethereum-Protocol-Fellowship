---
timezone: Asia/Dubai
---

# lllapland

1. 自我介绍
   大家好我是 lllapland，爱好和饭碗都是写代码，智能合约萌新。

2. 你认为你会完成本次残酷学习吗？
   根据以往经验不会完成，但是我会尽力完成。我自控力比较差，一般被push的时候效果最好（逃）。

## Notes


<!-- Content_START -->

### 2025.02.06

https://epf.wiki/#/eps/week1

#### Prehistory and Philosophy

- Free Software movement
  - **UNIX** (1960s): Modular design, key to Ethereum's architecture; Bell Labs' open collaboration mirrors Ethereum's core development.  
  - **Free Software Movement**: Led by Richard Stallman, emphasizing software freedom and open source principles
  - **FOSS (Free & Open Source Software)**: Software that respects users' freedom and community
  - **GNU**: Foundation for open-source software, influencing Ethereum's development principles. GNU stands for "GNU's Not Unix"
- Cryptography
  - **Key Usage**  
    - Symmetric: Same key for encryption & decryption  
    - Asymmetric: Uses a public/private key pair  
  - **Security**  
    - Symmetric: Less secure if the key is exposed  
    - Asymmetric: More secure; only the private key must be kept secret  
  - **Speed**  
    - Symmetric: Faster (simpler computation)  
    - Asymmetric: Slower (complex mathematical operations)  
  - **Key Distribution**  
    - Symmetric: Requires secure key exchange  
    - Asymmetric: Public key can be shared openly  
  - **Common Algorithms**  
    - Symmetric: AES, DES, RC4  
    - Asymmetric: RSA, ECC, Diffie-Hellman  
  - **Use Cases**  
    - Symmetric: Encrypting files, database security  
    - Asymmetric: Digital signatures, 🌟 **blockchain**, secure communication (TLS, PGP)  


#### Implementations and Development
- **Clients**: Implementations of the Execution Layer (EL) or Consensus Layer (CL).
  - EL clients: Geth, Nethermind, Besu
  - CL clients: Prysm, Lighthouse, Teku
- **Nodes**: Computers running both an EL and CL client, actively participating in the Ethereum network.
#### Ethereum Roadmap Phases  
- **The Merge** Transition from Proof of Work (PoW) to Proof of Stake (PoS).  
- **The Surge** Scalability improvements with **rollups** and **sharding**.  
- **The Scourge** Addressing censorship resistance and decentralization issues.  
- **The Verge** Introduction of **Verkle Trees** to optimize data storage.  
- **The Purge** Pruning old state data to reduce node storage requirements.  
- **The Splurge** Miscellaneous upgrades and optimizations.  

---
### 2025.02.07

https://epf.wiki/#/eps/week2

#### Execution Layer

##### Block Validation
```typescript
stf(parentBlock: Block, curBlock: Block, state: State): [State, Error]
```
- `stf` -> state transition function
- verify header
  - merkle roots
  - gas limit
  - timestamp
  - etc.
- verify and process a block
##### Block Building

```typescript
build(env: Environment, pool: TransactionPool, state: State): [Block, State, Error]
```
- construct a new block from environment, transaction pool, and current state


### 2025.02.09

#### Execution Layer

##### Uncle Blocks
- valid blocks that were mined but not included in the canonical chain ( usually due to network delays or simultaneous block production by multiple miners)
  - Why exist?
    - for miners to include uncle blocks in new blocks and receive **additional rewards**
    - to improve security and reduce centralization by compensating **valid but orphaned blocks**


##### Modern Ethereum Execution Clients

| **Client**     | **Language** | **Why Chosen?**                                      |
|---------------|-------------|------------------------------------------------------|
| **Geth**      | Go          | Easy concurrency, large developer community, mature ecosystem |
| **Erigon**    | Go          | Optimized storage, improved sync speed 💡         |
| **Nethermind** | C#         | Suitable for .NET ecosystem, enterprise-friendly   |
| **Besu**      | Java        | Hyperledger compatibility, enterprise-level support |
| **Reth**      | Rust 💡       | High performance, memory safety                     |


##### Consensus Layer vs. Execution Layer

| **Comparison**      | **Execution Layer (EL)**            | **Consensus Layer (CL)**       |
|---------------------|----------------------------------|----------------------------------|
| **Main Function**   | Processes transactions, executes smart contracts | Validates blocks, runs **PoS** consensus |
| **Core Components** | EVM, Transaction Pool, State Database | Beacon Chain, Validators, Slot/Epoch Mechanism |
| **Runs PoS?**       | ❌ No | ✅ Yes |
| **Consensus Role**  | Executes transactions but does not determine consensus | Runs PoS rules, decides block validity |
| **Client Examples** | Geth, Erigon, Nethermind | Prysm, Lighthouse, Teku, Nimbus |
| **Stored Data**     | Account balances, smart contracts, transaction history | Validator registry, voting data, finality information |

##### Why Did Ethereum Split CL and EL?

Before **The Merge**, Ethereum used a **PoW (Proof of Work) + Execution Layer** model, where a single client handled both **consensus (mining) and transaction execution**, leading to several issues:

- High computational cost (electricity).  
- Slow blockchain synchronization (the continuously growing state increased sync time).  
- Inefficient consensus mechanism (PoW was difficult to optimize).  

After **The Merge**, Ethereum split into **Execution Layer (EL) + Consensus Layer (CL)**, offering key advantages:  
- Execution Clients focus on **transaction execution and performance optimization**
- Consensus Clients handle **PoS rules**, improving **security and decentralization**
- EL and CL can be upgraded **independently**, enhancing **flexibility** 🌟

##### How Do CL and EL Communicate?

via the **Engine API**, 

1. **CL** requests **EL** to provide a new block
2. **EL** executes the block and returns the execution result
3. **CL** decides whether to accept the new block through validator voting.  

##### EVM
![EVM](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*a4cYYJZLlObtCGMIDiQeKQ.png)

- arithmetic (add, mod, etc.)
- bitwise 
- environment (block context, etc.)
- system (call, create, storage, return, etc.)
- control flow (branch, jump, etc.)
- stack (push, pop, etc.)
- memory (load, store, etc.)

##### p2p
- Execution layer operates** on devp2p (ethereum's p2p protocol).
  - **devp2p** allows nodes to support different **sub-protocols**:
    - **eth/68, eth/69** – for transaction and state synchronization.
    - **snap** – for fast state synchronization.
      - optimizations:
          1. **quickly syncing new nodes** by fetching **flat state data** instead of reconstructing the Merkle Patricia Trie.  
          2. uses **batch requests** (`GetAccountRange`, `GetStorageRanges`) to efficiently retrieve account and contract storage data.  
          3. **reduces disk I/O** by eliminating deep MPT traversals, improving sync speed. 
      - outcome:
        - enables nodes to complete state synchronization in **3-6 hours instead of days**.      
    - **les** – for light clients.
  - features  
    - efficiently communicate and synchronize data.
    - support different types of clients (full nodes, light clients, etc.) 💡
- **Responsibility**
  1. historical data
    - `GetBlockHeader`
    - `GetBlockBodies`
    - `GetReceipts`
    - etc.
  2. pending transactions
    - `Transactions`
    - `NewPooledTransactionHashes`
      - notifies peers of new pending transactions by sharing only their transaction hashes, reducing bandwidth usage
    - `GetPooledTransactions`
    - etc.
  3. state

    

  

<!-- Content_END -->
