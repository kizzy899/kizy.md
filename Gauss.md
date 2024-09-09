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

# {你的名字}

1. 自我介绍

我是gauss，希望通过本次共学能学习到更多关于web3的知识
   
2. 你认为你会完成本次残酷学习吗？

我会尽力的:D

## Notes

<!-- Content_START -->

### 2024.09.07

**Aptos区块链概述**

Aptos区块链使用拜占庭容错（BFT）共识协议，验证节点通过该协议就已完成的交易和其执行结果达成一致。验证节点决定哪些交易将被添加到区块链以及其顺序，并在本地维护最新的区块链状态。

验证节点在一个私有网络中直接相互通信，而完整节点则充当已确认交易历史的外部验证或传播资源。完整节点可重新执行交易以验证其正确性，并在发现问题时提供证据，防止验证节点的腐败或串通。

AptosBFT共识协议能够容忍最多三分之一的恶意验证节点。

验证节点的主要组件
- Mempool：一个存储尚未达成共识或执行的交易的内存缓冲区。通过mempool，各节点间可以共享这些待处理的交易。mempool还负责验证新交易的合法性，并防止拒绝服务攻击（DOS）。
- 共识（Consensus）：负责在网络中各验证节点之间达成共识，确定交易块的排序并就执行结果达成一致。临时成为领导者的验证节点从mempool中提取交易，提出新的交易块，并广播给其他验证节点。
- 执行（Execution）：负责协调交易块的执行并维护暂时状态，直到共识达成并提交块到分布式数据库。执行组件与虚拟机协作，以确保交易的执行。
- 虚拟机（VM）：运行每笔交易中的Move程序，决定执行结果。mempool使用虚拟机进行交易的初步验证，而执行组件使用虚拟机来实际执行交易。
- 存储（Storage）：用于将达成共识的交易块及其执行结果持久化到本地数据库。
- 状态同步器（State Synchronizer）：确保节点能够“追赶”区块链的最新状态并保持最新。

### 2024.09.08

在Aptos区块链中，账户代表对一组资产（如链上货币和NFT）的访问控制。这些资产由Move语言中的一种原语（称为资源）表示，强调了访问控制和稀缺性。

**账户类型和特点**

标准账户：对应于一个地址和公钥/私钥对的普通账户。

资源账户：不与任何私钥相关的自主账户，用于开发者存储资源或发布链上模块。

对象：在单一地址内存储的一组复杂资源，表示单个实体。

Aptos中的账户是显式的，需要在执行交易之前被创建。

账户创建可以通过显式调用或通过向账户地址转入Aptos代币（APT）进行隐式创建。

**账户的独特功能**

旋转认证密钥：账户的认证密钥可以更改为由不同的私钥控制，类似于Web2世界中的更改密码。

原生多重签名支持：支持k-of-n多重签名，使用Ed25519和Secp256k1 ECDSA签名方案。

**账户地址**

Aptos中的账户地址是32字节的十六进制字符串，通常显示为64个十六进制字符。

支持使用Aptos Name Service来获取.apt域名，使账户更易于识别和记忆。

**创建账户的步骤**

选择认证方案（如Ed25519或Secp256k1 ECDSA）。

生成新的私钥和公钥对。

将公钥与认证方案结合生成32字节的认证密钥和账户地址。

使用私钥为该账户签署交易。

**认证密钥**

初始的账户地址设为在账户创建时生成的认证密钥。

认证密钥可以在生成新的公私钥对时更改，但账户地址不会改变。

Aptos支持多种认证方案，包括Ed25519、Secp256k1 ECDSA、K-of-N多重签名和多Ed25519方案（遗留方案）。

**多重签名与通用认证**

K-of-N多重签名：有N个签名者，至少K个签名用于认证交易。

通用认证：支持Ed25519和Secp256k1 ECDSA认证方案，允许多种密钥组合。

**密钥旋转**

Aptos账户可以通过account::rotate_authentication_key函数更换密钥，以防止已泄露的密钥被滥用。

**账户状态**

每个账户的状态由代码（Move模块）和数据（Move资源）组成。

Move模块：包含代码（如类型和过程声明），但不包含数据。

Move资源：包含数据，但不包含代码，表示区块链上的全局状态更新规则。

**访问控制与签名者**

在Aptos Move中，交易的发送者由signer表示。signer参数在Move模块的函数中用于访问控制，确保只有授权的账户才能执行某些操作。



<!-- Content_END -->
