---
timezone: Asia/Tokyo
---


---

# Newraina

1. 自我介绍
我是 Newraina

2. 你认为你会完成本次残酷学习吗？
会

## Notes

<!-- Content_START -->

### 2024.08.31

完成报名。

### 2024.09.07

共识机制
- AptosBFT
- 拜占庭容错

账户模型
- 地址格式：32字节的十六进制字符串
- 显式账户，需要先创建账户，然后才能交易
  - 认证私钥可修改，类似修改密码
  - 支持多签
- 三种账户
  - 标准账户
  - Resource 账户
  - Object 账户， address 就是 ObjectID
- Ed25519 和 Secp256k1 ECDSA
  - 两种不同的椭圆曲线签名算法
  - Ed25519 更快，更节省空间，更安全
  - Secp256k1 在比特币和以太坊中使用

### 2024.09.09

资源模型

- key 能力的 Struct 被视为 Resource，可以存储在账户或者全局存储里
- store 能力的 Struct 可以被存储在其他 Resource 里

```move
struct Coin has key {
  value: u64
}

struct CoinStore has key {
    coin: Coin,
}

CoinStore 是 Resource，Coin 是代币本身，可以存储在 CoinStore 里。

```

### 2024.09.10

尝试部署一个合约到 devnet：

https://explorer.aptoslabs.com/txn/0x122e90a603d7dba158a5cc564c3858a96723d50d92b7aba22c63aae740db3602?network=devnet




<!-- Content_END -->
