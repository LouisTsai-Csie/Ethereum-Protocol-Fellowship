---
timezone: Asia/Shanghai
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# 奕 iyi

1. 自我介绍：一名 后端 Golang、Node.js、Rust 开发者; 合约 ETH、Arb、Solana 开发者。进入 web3 行业 2 年
2. 你认为你会完成本次残酷学习吗？会

## Notes

<!-- Content_START -->

### 2025.02.06

1. 今天快速 了解 EPF（Ethereum Protocol Fellowship ） wiki 是什么： ethereum protocol 资源的集合。包含 2 部分
   1. Protocol Study Group
   2. Protocol Wiki

### 2025.02.07

1. 学习小组的内容分为 2 部分：前 2 周 学习已有的课程，后面 6 周 是讲座。 后面的主要学习已有的课程
2. 学习小组的内容 可以去对应的 github 去贡献：https://github.com/eth-protocol-fellows/protocol-studies

### 2025.02.08

1. Week0: 前置准备工作： 密码学、默克尔树数据结构、网络 p2p 分布式系统、软件开发基础、以太坊平台

### 2025.02.09

1. Week1: 协议和生态的基本介绍
   1. 为了理解 Ethereum 的设计，需要提前了解之前的历史 和对应的文化建立：自由软件运动、非对称密码技术的发明
   2. Ethereum 协议的设计最初来源 V 神的 blog, 灵感来自 BTC 把 ETH 设计为一个通用的 区块链计算平台
   3. https://ethereum.org/en/quizzes/ 这个地址可以测试对 以太坊资料的了解程度

### 2025.02.10

1. Week2: 以太坊 执行层 EL
   1. Block validation
      1. 处理相关状态状态的过渡
      2. 每个交易都有 执行层客户端 验证、执行 保存结果到状态树里面
      3. 新的节点节点接入 还必须丝滑，提供了有效的同步机制引导
   2. Block building
      1. 根据网络中的交易，创建交易快
      2. p2p tx pool
2. JSON-RPC
   1. 远景是所有的客户端提供相同的 api, 用户可以运行他们选择的任意客户端，并于所有工具完美集成

### 2025.02.11

1. Week3:  共识层 CL 是以太坊的一个核心组件，核心任务使用 Pos (Proof of Stake) 来确保网络中的安全性、一致性、去中心化
   1. 负责共识算法：验证者选择、区块提议、区块验证、最终性
   2. 确保每个交易只只能包含在一个区块终
   3. 奖惩机制
   4. 网络同步
   5. 主要的参与者是验证者

### 2025.02.12

1. Week4: 主要讲测试和安全方面
   1. 存在很多工具，都没有用过啊，感觉有点头大

### 2025.02.13

1. 今天发现 下面的 Protocol Wiki 对应上面的每一周的内容
2. 今天发现 再 ETH 架构图里面 有一个 Beacon APIS 的东西，一组 HTTP API 接口。 总得来说 就是把共识层相关的能力和数据通过  API 接口暴露出去
   1. 可以查询链上数据：最新区块信息，查询验证者状态等
   2. 提交验证者的证明、提交区块的提议
   3. 监控和调试
   4. 治理和配置


<!-- Content_END -->
