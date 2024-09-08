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

# {Punkcan}

1. 自我介绍
	1. 单纯喜欢Aptos的设计，自学Aptos中
2. 你认为你会完成本次残酷学习吗？
	1. 可以，一定可以，一年总得要有个Flag完成吧

## Notes

<!-- Content_START -->

### 2024.09.07

就我理解到的Aptos特点
- 模组化设计，这也是比较吸引我的，主要是安全管理，当一个模组被判断为安全时，后续沿用模组就没有安全上的顾虑
- Block-STM，一种并行方式，可以为整个链的吞吐量提供弹性（但细节我还不清楚）
- 储存模式，EVM的储存是所有用户的数据都储存在一个合约中，如果是Mapping还好但如果是数组等数据，会随着时间的演进，效能越来越差，但是Aptos的数据是储存在用户的帐号上，提升了并行条件跟执行效率（当然如果ORE这类的去干他，我不确定会不会也被干挂）
- AptosBFT，共识基于拜占庭共识协议设计，有快速验证，快速恢复的特性

Move上模组更新的时机点：
- Move语言更新
- MoveVM更新

##### Aptos是什么？

Aptos 的历史可以追溯到 Facebook 于 2019 年发布的区块链项目 **Libra**。
Libra 旨在推出一种全球化的数字货币，并计划与各大国际企业、金融机构合作。
希望能通过区块链技术构建一个可扩展的支付网络，支持全球数十亿用户的跨境交易。

然而，由于监管压力和各国政府对稳定币的担忧，Libra 项目在多方阻力下经历了多次修改和调整，最终于 2020 年更名为 **Diem**，并将项目重心从全球货币转移到更加合规和可监管的支付系统上。尽管进行了调整，Diem 仍然面临着监管挑战，最终 Meta 于 2022 年决定终止该项目。

在 Diem 项目停止之后，**Aptos Labs** 由前 Diem 团队成员成立，特别是区块链研究人员 **Mo Shaikh** 和 **Avery Ching**，他们是 Diem 项目中负责技术架构和开发的关键人物。
Aptos 的目标是延续 Diem 的技术优势，并将其打造为一个面向开发者和用户的高性能公链。

（另外还有一组人是Sui，他们更着重在数据结构的设计，两者使用的加密跟共识法并不一样，虽然开发都是Move）

Aptos 的技术架构继承了 Diem 的诸多核心理念，并进一步优化了这些技术，尤其是在共识协议、并行执行、智能合约和安全性方面。

- **Move 编程语言**：Aptos 延续了 Diem 开发的 Move 语言，作为其智能合约编程语言。Move 的资源管理和安全特性，使其成为一个高度可靠的区块链编程语言。
- **高性能共识机制**：Aptos 基于 Diem 的 **HotStuff 共识协议**，并通过优化改进为 AptosBFT，共识速度更快，吞吐量更高。
- **并行交易执行**：Aptos 的并行执行引擎 **Block-STM**，允许多个交易同时处理，极大提高了链上交易的效率。

Aptos 在项目启动后，迅速得到了区块链领域的广泛关注。2022 年，Aptos 通过多轮融资，获得了大规模的资金支持。参与投资的著名机构包括 **a16z（Andreessen Horowitz）**、**Multicoin Capital**、**FTX Ventures** 等。

- **2022 年 3 月**：Aptos 宣布完成了 2 亿美元的融资，由 a16z 领投，其他知名风投公司如 Multicoin Capital 和 Coinbase Ventures 参与。
- **2022 年 7 月**：Aptos 再次获得 1.5 亿美元的融资，这次融资由 FTX Ventures 和 Jump Crypto 领投，使得其估值大幅提升。

这些融资帮助 Aptos 构建了一个强大的开发生态，并推动了技术的进一步迭代和创新。

经过数月的开发和测试，Aptos 于 **2022 年 10 月 17 日** 正式推出其主网，命名为 **Aptos Autumn**。在主网上线之前，Aptos 已经通过多轮测试网和社区的合作，完善了基础设施、开发工具和网络安全性。


自主网上线以来，Aptos 致力于构建一个强大的开发者和用户生态系统。其愿景是成为支持去中心化金融（DeFi）、游戏、NFT 和其他去中心化应用的核心基础设施。

- **开发者友好性**：Aptos 通过提供详细的开发文档、工具和资源，吸引了大量开发者社区的参与，并且许多项目基于 Aptos 开发智能合约和去中心化应用。
- **合作伙伴与集成**：Aptos 与多个主流项目和企业达成了合作，以推动生态系统的扩展，并且吸引了包括开发工具、钱包、桥接工具、和去中心化交易所在内的多个合作伙伴。


不过我觉得目前节点的中心化程度有点高，这似乎是近期在各个公链的一些现象

### 2024.09.08
### 2024.09.09
### 2024.09.10
### 2024.09.11
### 2024.09.12
### 2024.09.13
### 2024.09.14
### 2024.09.15
### 2024.09.16
### 2024.09.17
### 2024.09.18
### 2024.09.19
### 2024.09.20
### 2024.09.21
### 2024.09.22

<!-- Content_END -->
