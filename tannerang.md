---
timezone: Asia/Shanghai
---

---

# Tanner

1. 自我介绍
Hi, I'm Tanner. I'm excited to dive deeper into the Ethereum protocol and can't wait to learn more at this event!
1. 你认为你会完成本次残酷学习吗？
As much as I can.

## Notes

<!-- Content_START -->
### 2025.02.06

完成 week0 和部分 week1 內容
瀏覽 epf.wiki 一些內容，有很多典故是第一次聽，對於歷史有更宏寬的了解
同時也去底下連結做了些有關乙太坊的題目順便複習
https://ethereum.org/quizzes

### 2025.02.08

瀏覽 Execution Layer 的 EL Spec，順便複習 EIP-1559 在做什麼。

EIP-1559
- 引入動態 baseFee 的機制來做到費用可預測性和優化尖峰時期使用體驗
- 改變了原有 gas 費用結構，一是引入 baseFee 且其值會根據當前區塊的需求而浮動，二是用 priorityFee 作為激勵礦工優先處理交易的小費
- 當一區塊 gas 的使用程度超過 50%，baseFee 將上升，反之則下降，最大漲跌為 12.5%，其中，若新的區塊持續保持最大使用量，將在 200 block 達到 baseFee = 1 Ether
- baseFee 將被 burn 掉，而不是支付給驗證者，燃燒可以減少總供應量，藉此降低通膨壓力

<!-- Content_END -->
