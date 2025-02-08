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
- verify and process a block
##### Block Building

```typescript
build(env: Environment, pool: TransactionPool, state: State): [Block, State, Error]
```
- construct a new block from environment, transaction pool, and current state

---


TBC
赶灰机去了


<!-- Content_END -->
