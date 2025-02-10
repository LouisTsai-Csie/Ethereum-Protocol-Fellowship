---
timezone: Asia/Shanghai
---


---

# realgu

1. 在金融行业做软件开发。去年看了许多v神文章，大为振奋，在3700大举买入以太，并持有至今 ：）推特账号 @0xrealgu 欢迎互关
2. 之前完成过链上叙事共学，这次应该也没问题，期待

## Notes

<!-- Content_START -->

### 2025.02.06

看完了week1 writeup，有许多不错的参考资料链接，有空慢慢看

### 2025.02.07
边看边记：
- execution layer and concensus layer are actually two different clients, each have its own p2p network
- 重点研究: trie, merkle trie/tree, patricia trie, merkle-patricia trie, verkle trie 把leetcode150里面trie的题做了

### 2025.02.09
- trie: also known as prefix tree, 做一道题就全明白了 [check this](https://leetcode.com/problems/implement-trie-prefix-tree?envType=study-plan-v2&envId=top-interview-150)
- Patricia trie: a trie in which each node that is the only child is merged with its parent. [check this](https://en.wikipedia.org/wiki/Radix_tree)
- Merkle tree: a tree of hashes. [check this](https://www.investopedia.com/terms/m/merkle-tree.asp) Bitcoin's software does not run the entire block of transaction data through the hash function all at once. Rather, each transaction is hashed, then a pair of transactions is concatenated and hashed together, and so on, until there is one hash for the entire block. If there is an odd number of transactions, one transaction is doubled, and its hash is concatenated with itself.
- why don't we just have a hash of all transactions concatenated? why do we run a lot more hashes by building a merkle tree? The Merkle tree is useful because it allows users to verify a specific transaction without downloading an entire blockchain—which can be hundreds of gigabytes in size. For example, say that you wanted to verify that transaction TD is included in the block in the diagram above. If you have the root hash (HABCDEFGH), you can query the network about HD. It might return HC, HAB, and HEFGH. The Merkle tree allows you to verify that everything is accounted for with three hashes: given HAB, HC, HEFGH, and the root HABCDEFGH, HD (the only missing hash) has to be present in the data. Additionally, the structure is helpful because the process is very fast. It seems as if hashing thousands of transactions would be time-consuming, but modern computers can do it in milliseconds. Because it is easy for computers to do, it makes sense to use the technique to verify large amounts of data, like the data contained in a blockchain. Merkle roots, trees, and block hashes are what create the unalterable chain of transactions and blocks.
- merkle-patricia trie [checkthis](https://ethereum.org/en/developers/docs/data-structures-and-encoding/patricia-merkle-trie/)

<!-- Content_END -->
