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
- wiki的知识点感觉有点零散，读《Absolute Essentials of Ethereum》梳理下整体脉络。
- **Ch2. Execution Layer**
	- Ethereum address are 42-character hexadecimal identifiers derived from the last 20 bytes of the public key with 0x prefix.
		- more intuitive and user-friendly account experience called **Account Abstraction**
	- EOA
		- address + associated account state
		- contains two fields:
			- **Nonce**, is an increasing number showing how many transactions an account has made and how many contracts it has created. It is used to determine the order of transactions in the same slot.
			- **Balance**, how much ETH is holding.
	- Contract Accounts
		- are smart contracts that have been deployed on Ethereum and are controlled by their own internal code.
		- Ethereum address + associated account state
		- contain a state of four fields:
			- **Nounce**, incremeting number showing how many contracts the contract account has created ??
			- **Balance**, how much ETH the contract account is holding
			- **Code**, is the smart contract code contained in the account
			- **Storage**, maps the contents of the contract account. When a transaction involving a contract account is processed, the changes are recorded permanantly in the contract's Storage.
	- Transactions (two types)
		- Message Call
			- Value, ETH
			- Input Data
				- EOA-EOA, arbitrary Data, perhaps to send a message or tag a transaction. *Usually is left empty*
				- EOA-contract, contract-contract, includes the contract's Code  to be invoked and any proposed changes to Storage.
		- Contract Creation
			- request a new contract account to be added to the Ethereum world state.
			- sent to an empty address since there's no recipient
			- once initialised, are a combination of the sender's address and the last Nonce from the sender's account
	-

### 2025.02.11
- 《Absolute Essentials of Ethereum》Ch2 **Execution Layer**
	- **Ether & Transaction Fees**
		- Gwei is used to denominate transaction fees.
		- **gas cost** and **gas fees**. In Ethereum, computational cycles are calculated in a unit call gas. A gas unit is not a currency unit. Gas cost relates only to how many computational cycles are needed.
		- *Every computational instruction(an Opcode) in a transaction has an associated gas cost.*
		- The Gas Limit included in a transaction is the maximum amount of gas that a user is willing to pay for.
		- Gas fees have two forms.
			- **base fee**, refers to the algorithmically dynamic cost of gwei in the Ethereum network
			- **priority fee**, get transaction accepted faster
		- Transaction fees = gas cost * (base fee + priority fee)
		- The above is pre-2021 situtaion(London Upgrade/EIP-1559)
		- The base fee is burnt and removed from circulation.
		- The priority fee is paied to the users called validators.
	- **Transaction Structure**
        | Field | comment |
        |---|---|
        | From | sending address |
        | To | receiving address |
        | Digital Signature | a signature produced using the private key of the sender |
        | Nonce | show how many transactions an account has made |
        | Value | the ETH to be transfered |
        | Input Data | Input data(message call) ; Initialise(contract creation) |
        | Gas Limit | limit on gas |
        | Max Priority Fee | maximum priority fee you will pay |
        | Max Fee | maximum overall fee you will pay |
    - **Ethereum Virtual Machine(EVM)**
		- the most important field is the **Input Data**, because it contains the function we want to call and the arguments we want to pass.
		- it follows Application Binary Interface(ABI) format.
		- functions are identified in the ABI specification by the reference MethodID.
		- `transfer(address to, uint256 value)`
			- MethodID: `0xa9059cbb`
			- ByteCode: `0xa9059cbb00000000000000000000009f11260cb6427c20a019780d99d3a2d7ffe9a25300000000000000000000000000000000000000000000000000002c8650c0`
		- The EVM interprets and executes the Input Data field using the following:
			- **Virtual Read-Only Memory(ROM)**: Reads the code of an involved contract account
			- a temporary state for processing the transactions:
				- **Program Counter**: The program counter tracks what instructions from the contract code need to be processed next
				- **The Stack**: The EVM uses a stack-based model for executing code
				- **EVM Memory**: Temporary memory used within the machine state to track changes
				- **Gas counter**: Tracks the gas used. Reverts if no more gas is available and undoes the proposed state changes.
			- **Storage**: changes are recorded permanently to reflect the new world state that emerges from the temporary machine state.
	- **ERC-20**
		- The ERC-20 token standard creates fungible tokens.
	- **ERC-721**
		- ERC-721 is designed to create Non-Fungible Tokens(NFT). *ERC-721 tokens are unique.*
		- usually an NFT smart contract builds a collection of items that are a similar type, but with unique differences.
	- **Decentralised Application(dApps)**
		- In an Ethereum context, a dApp refers to the smart contract plus the non-blockchain technologies it combines with to aid the user experience.

### 2025.02.12

### 2025.02.13

### 2025.02.14

### 2025.02.15

### 2025.02.16
<!-- Content_END -->
