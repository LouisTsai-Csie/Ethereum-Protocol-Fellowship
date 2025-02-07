---
timezone: America/New_York
---

# 0xKJ

1. 自我介绍
    - Dr KJ，密码学和共识算法博士，Useful PoW 和 Minus Theory 发现者。
    - 近期向以太坊提出扩容方案 https://ethresear.ch/t/l1-improvement-based-on-minus-theory/21494
    - 由于仅仅熟悉 PoW 以太坊机制，对于 PoS 并不是太理解。所以来补课，并且试图搞清楚以太坊 L1 扩容的可能性和技术细节。

2. 你认为你会完成本次残酷学习吗？
    - 不一定！

## Notes

<!-- Content_START -->

### 2025.02.06

今天是首次参加残酷共学，由于基本上我已经手撸过一个完整的POW区块链了，对以太坊的虚拟机和MPT也有过动手经验，所以这次会主要把注意力放在之前不太熟悉的POS知识上，也希望能结合到代码层面，弥补对 https://github.com/ethereum/go-ethereum 和 https://github.com/prysmaticlabs/prysm 的认知。

今天主要熟悉 The Protocol 部分, 值得一看的主要是 https://epf.wiki/#/wiki/protocol/architecture ，在转向POS之后，仅仅运行geth已经不够，还要结合 prysm 运行 Beacon Node。
第一张图中User APIs可以理解为ETH RPC，以前我实现过 https://github.com/EcoPoW/BitPoW/blob/master/eth_rpc.py

Beacon APIs 和 validator 连接，结合这两天看的油管视频，prysm应该是可以运行成 Beacon Node 或者 validator 模式的，所以这里的 validator 应该是用来验证 POS 谁有权出块的验证，而不是对整个区块链或者 EVM 执行结果的验证。

Engine API 是 geth 和 prysm 之间通信的API，暂时还不知道具体工作内容。但是可以知道，如果 POS 算法得知当前节点现在有出块权，prism 应该第一时间主动通知 geth 切换到出块模式。

代码可以看到 https://github.com/prysmaticlabs/prysm/tree/develop/cmd 有 beacon-chain 和 validator 模式，以及其它模式。每个都会有对应的`main.go`代码。在运行 `func main` 之后进入 `func startNode`，`node.New` 和 `beacon.Start` 之后应该就跳转到https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/node/node.go 去了。

今天就先研究到这里。

### 2025.02.07

从 https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/node/node.go 中的 `beacon.Start` 跳转到
https://github.com/prysmaticlabs/prysm/blob/develop/runtime/service_registry.go#L42 `StartAll`, 这里顺便学习一下 Go 语言的 `go` 关键字用来启动 coroutine。软件工程里的很多东西还真的得有调试环境和 log 才能更容易的学习到。这里光靠读代码已经跟丢了，所以这就是我们未来实现工程需要避免的地方，写普通人能读的代码！尤其是区块链开源。

https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/node/node.go#L203 我们在 `func New` 里找到了 `func registerServices`

休息一下……我们遇到了分叉路口，需要好好思考一下接下来读哪些代码？

直接从名字猜吧：
 * P2P Service 顾名思义，P2P广播网络
 * [Backfill Service](https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/sync/backfill/service.go) 进代码看了一下，好像和slot有关系，也和同步有关系
 * POW Chain Service 向前兼容
 * [Attestation Pool Service](https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/operations/attestations/service.go) 见证，可能和 PoS 有关系
 * Blockchain Service 名字起的太泛泛了
 * Initial Sync Service 首次同步之后要做些什么？
 * Sync Service 很明显
 * [Slashing Pool Service](https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/operations/slashings/service_new.go) 和 POS 质押有关系
 * [Slasher Service](https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/slasher/service.go#L84) 和质押有关系
 * builder service 猜测这里的 builder 就是区块链新 block 的 builder 的意思
 * RPC Service 很好懂
 * HTTP Service 很好懂，可以看看有什么API在里面
 * Validator Monitoring Service 很好懂
 * Pruner Service 历史数据库删除？

经过一下午的研究，我大致确认 Slasher Service 才是我要研究的代码，应该是 PoS 逻辑最主要的部分。
Attestation Pool Service 似乎和区块分叉的选择有关系。
Slashing Pool Service 则是 Slasher Service 的依赖模块。

### 2025.02.08

继续阅读代码，由于没有本地搭建编译和调试环境，所以以阅读为主，不求甚解。

https://github.com/prysmaticlabs/prysm/blob/develop/beacon-chain/slasher/service.go#L88 首先是这个 `func (s *Service) run()` 阅读这里的逻辑。这里在做并行系统的人，需要有一种代码感受，因为做 beacon 是一个分布式系统，所以slash的逻辑需要在很多 beacon nodes 上一起执行，并且得到相同结果。

带着问题去看以上的代码，尝试把关于POS的一些基本问题定位到具体代码逻辑：什么时候质押（比如32个ETH）会被罚没呢？这会反向让我们跳出代码来思考问题本身。

感受到了知识的缺乏以后，开始在网上搜索，找到了 prysm 自己的官方 doc https://docs.prylabs.network/docs/install/install-with-script 在这方面学习更多对 POS 的基本概念。

### 2025.02.09

<!-- Content_END -->
