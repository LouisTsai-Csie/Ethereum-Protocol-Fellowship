---
timezone: Asia/Shanghai
---

# mrmign

1. Web2->Web3新人，之前学习过Sui和Move，但是理解不够深。想要深入理解区块链生态还是要从以太坊开始。
2. 你认为你会完成本次残酷学习吗？ Yes, Just do It!

## Notes

<!-- Content_START -->

### 2025.02.06
### Learning general concepts:
Learn [Inevitable Ethereum - World Computer](https://inevitableeth.com/home/ethereum/world-computer)
- Btc came up the promise: fair payments, for anyone, at any time, forever
- The World Computer is made of up 3 parts:
	- Ethereum Virtual Machine (EVM)
		- a Turing-complete distributed state machine
	- Ethereum Blockchain
		- A [block](https://inevitableeth.com/home/ethereum/blockchain/block) is made up of 3 key components:
			- A record of the [transactions](https://inevitableeth.com/home/ethereum/blockchain/transaction) executed at the time the block was created
			- A [signature](https://inevitableeth.com/home/concepts/digital-signatures), unique to each specific block
			- A reference to the previous block's signature
	- Ethereum Network
		- is made up of a group of people and institutions who decide to run an Ethereum node
		- A single node runs two pieces of software:
			- a consensus client
			- an execution client (responsible for operating the EVM)
		- PoS(2022) <- PoW(2015)
			- Stake 32ETH to become a validator

### 2025.02.07
- Ethereum Accounts
	- the information("state") that the blockchain keeps track of is make up of accounts.
	- Two types of accounts:
		- Externally owned account(EOA), represents the user
		- Contract, a computer program that lives on-chain
- Gas
	- Gas is the "unit" of resource consumption within Ethereum
- Ethereum fundamental principles:
	- Simplicity
	- Universality
	- Modularity
	- Non-discrimination
	- Agility
- [The vision for the Ethereum roadmap](https://twitter.com/VitalikButerin/status/1741190491578810445)
	- **The Merge**: upgrades relating to the switch from proof-of-work to proof-of-stake
	- **The Surge**: upgrades related to scalability by rollups and data sharding
	- **The Scourge**: upgrades related to censorship resistance, decentralization and protocol risks from MEV
	- **The Verge**: upgrades related to verifying blocks more easily
	- **The Purge**: upgrades related to reducing the computational costs of running nodes and simplifying the protocol
	- **The Splurge**: other upgrades that don't fit well into the previous categories.

### 2025.02.08
- ### Week2 Pre-reading
- ### Nodes and clients
	- Node Types
		- Full node
			- Full nodes do a block-by-block validation of the blockchain, including downloading and verifying the block body and state data for each block
		- Archive node
			- Archive nodes are full nodes that verify every block from genesis and never delete any of the downloaded data.
		- Light node
			- Light nodes only download block headers. Any other information the light node requires gets requested from a full node.
	- Synchronization modes
		- Execution layer sync modes
			- Full sync
			- Fast sync
			- Snap sync
			- Light sync
		- Consensus layer sync modes
			- **Optimistic sync**, a post-merge synchronization strategy designed to be opt-in and backwards compatible, allowing execution nodes to sync via established methods
			- **Checkpoint sync**(weak subjectivity sync), It's based on assumptions of [weak subjectivity](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/weak-subjectivity/) which enables syncing the Beacon Chain from a recent weak subjectivity checkpoint instead of genesis


### 2025.02.09
### Execution Layer(Eth1)
- **核心功能**：
	- **交易处理**：
		- 执行层负责验证和执行用户发起的交易（例如转账 ETH、调用智能合约）。
		- 每笔交易需要支付 **Gas 费用**（以 ETH 计价），用于补偿网络的计算资源消耗。
	- **智能合约执行**：
		- 智能合约的代码在 **以太坊虚拟机（EVM）** 中运行，执行层通过 EVM 确保合约按预定逻辑执行。
		- EVM 是以太坊的“全球计算机”，所有节点运行相同的代码以保证一致性。
	- **状态管理**：
		- 执行层维护以太坊的全局状态（State），包括：
			- 账户余额（ETH）。
			- 智能合约的存储数据。
			- 账户的 nonce（防止重放攻击）。
	- **Gas 机制**：
		- 每笔交易需要指定 Gas Limit 和 Gas Price，Gas 用于限制计算资源的使用。
		- 如果 Gas 不足，交易会失败并回滚，但已消耗的 Gas 不会退回。
- **核心组件：**
	- **以太坊虚拟机（EVM）**：
		- EVM 是执行智能合约的沙盒环境，完全隔离且确定性（相同输入必得相同输出）。
		- 支持 EVM 兼容的智能合约编程语言（如 Solidity、Vyper）。
	- **账户系统**：
		- **外部账户（EOA）**：由私钥控制的用户账户，可发起交易。
		- **合约账户（CA）**：由代码控制的账户，存储智能合约的代码和状态。
	- **交易结构**：
		- 每笔交易包含以下关键字段：
			- `from`：发送者地址。
			- `to`：接收者地址（如果是合约创建，则为空）。
			- `value`：转账的 ETH 数量。
			- `data`：调用合约时的输入数据。
			- `gasLimit`：交易允许消耗的最大 Gas。
			- `gasPrice`：用户愿意支付的 Gas 单价。
	- **状态树（Merkle Patricia Trie）**：
		- 以太坊使用状态树存储所有账户和合约的状态，通过哈希保证数据的不可篡改性。
	- **执行客户端**：
		- 执行层的软件实现（如 **Geth**、**Nethermind**、**Besu**），负责处理交易、运行 EVM、维护状态等。

### 2025.02.10

### 2025.02.11

### 2025.02.12

### 2025.02.13

### 2025.02.14

### 2025.02.15

### 2025.02.16
<!-- Content_END -->
