---
timezone: Asia/Shanghai
---

---

# poyucheese

1. 自我介绍
   我是在DeFi領域學習的大學生
2. 你认为你会完成本次残酷学习吗？
   會
3. TG 联系方式：@cheeseyes

## Notes

<!-- Content_START -->

### 2025.02.06

#### [SGweek1](https://epf.wiki/#/eps/week1) and my background acknowledge of ethereum

##### history of ethereum

以太坊在2020年底啟用 Beacon Chain ，作為以太坊的共識層(Consensus Layer)並開始使用PoS。在2022年經過了一次 The Merge ，從 PoW 完全轉為 PoS 的共識機制，合併主網與 Beacon Chain ，在同一條鏈上執行和共識分層運行。

- Execution Layer 負責處理單一 block 內的交易、邏輯、Gas 等運算。
- Consensus Layer 負責 block 之間的排序，並確保最終性。

由於目前共識層需要執行層的數據支持，並且主網更新必須保持向後相容，兩層尚無法獨立運行，大量的鏈上交易拖慢速度，這也是目前致力於開發 Layer2 solution 的原因。

### 2025.02.07

#### [SGweek1](https://epf.wiki/#/eps/week1)

今天讀了 week 1 的內容，順便做了 [quiz](https://ethereum.org/zh/quizzes/) 測試自己對以太坊基礎架構的認識，發現我對一般節點和質押驗證者的區別還不夠了解，只要在客戶端運行並在線就能成為一般節點，不必質押 ETH 同時也不會獲得獎勵，而質押驗證者還負責參與共識和打包區塊，須質押 32 ETH 並且在線時間達 50% 以上才能在上線時得到交易費和質押獎勵，質押驗證者若違反共識機制 (**double proposal** or **double voting**)，會遭到罰沒 (Slashing) ，質押的 ETH 被沒收並被踢出驗證。

看到有關 ENS 域名的技術，但還不懂他的運作原理，明天繼續衝鋒。

### 2025.02.08

#### [SGweek2](https://epf.wiki/#/eps/week2)

今天看了 week 2 錄影的片段，介紹的是執行層和共識層的邏輯，這讓我想到曾經看到 PAXG 穩定幣，感興趣查到一種應用在分布式系統的共識算法 [**Paxos 算法**](https://www.youtube.com/watch?v=d7nAGI_NZPk) (不過兩者好像沒什麼關聯)，這種算法可以應用於分佈式資料庫來實現跨資料中心的一致性，但在區塊鏈方面，因為它是基於預先指定的節點投票，所以只能應用於私有區塊鏈，無法應用於公有區塊鏈。

### 2025.02.09

#### [SGweek2](https://epf.wiki/#/eps/week2)

繼續 week 2 的課程，感覺 EVM 的架構在執行和運算上有一些跟 CPU 類似的地方，但還是有本質上的不同，例如 EVM 是 stack-based 的，CPU 則是 register-based，為了確保正確的交易順序，傳統 EVM 與 CPU 不同，無法平行化，我有看到一些有關 Parallel EVM 的研究和技術，但這些研究看起來還有很多挑戰要克服，VM 的平行化感覺會是未來很值得深究的一個方向。

<!-- Content_END -->
