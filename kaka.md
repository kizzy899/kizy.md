---
timezone: Asia/Shanghai
---

---

# 卡卡

1. 自我介绍 <br>
   一名计算机技术爱好者，从事计算机安全领域的工作。不久前接触到区块链，被去中心化的愿景所吸引。打算深入学习相关的技术，期待与大佬们交流学习！
2. 你认为你会完成本次残酷学习吗？<br>
   包完成的，不完成倒立洗头！！！

## Notes

<!-- Content_START -->

### 2024.09.01
了解Aptos残酷共学的规则，并报名。

### 2024.09.07
学习内容：1) 参加会议; 2) 阅读文档，对Aptos初步了解; <br>
学习笔记：<br>
Aptos 上有三种类型的账户：标准账户、资源账户、对象。

Aptos区块链上的任何交易执行都需要支付手续费，该费用包括两部分：
1. 执行和IO成本：以Gas Units为单位进行计量，Gas Units的价格可能根据网络负载而波动。
2. 存储费：涵盖了在分布式区块链存储中持久存储验证记录的成本。以固定的$APT价格来衡量。

Aptos区块链存储三种类型的数据：
- 交易：交易表示区块链上的账户正在执行的预期操作（例如转移资产）
- 状态：（区块链账本）状态代表交易执行输出的累积，即存储在所有资源内的价值
- 事件：交易执行时发布的辅助数据

### 2024.09.08
**学习内容**：TypeScript SDK的使用，并实践模拟交易; <br>
**学习记录**：<br>
使用 TypeScript SDK 初始化一个项目:

```
npm init && npm add -D typescript @types/node ts-node && npx tsc --init && mkdir src && echo 'async function example() { console.log("Running example!")}; example()' > src/quickstart.ts
```
测试初始化：
```
npx ts-node src/quickstart.ts
```
按照aptos sdk：
```
npm i @aptos-labs/ts-sdk
```
模拟交易: 交易允许你修改链上数据或触发事件。<br>
一般来说，交易从构建到链上执行需要经历5个步骤：构建、模拟、签名、提交、等待。<br>
1、构建：创建一个交易
```typescript
const transaction = await aptos.transaction.build.simple({
	sender: sender.accountAddress,
	data: {
		// All transactions on Aptos are implemented via smart contracts.
		function: "0x1::aptos_account::transfer",  //这是什么？
		functionArguments: [destination.accountAddress, 100],
	},
});
```

2、模拟：可选的，在提交交易之前模拟交易，为了估算成本。

```
const [userTransactionResponse] = await aptos.transaction.simulate.simple({
	signerPublicKey: signer.publicKey,
	transaction,
});
```

3、签名：一旦交易建立并且费用合理，就可以使用`aptos.transaction.sign`签署交易。

```
const senderAuthenticator = aptos.transaction.sign{(
	signer: sender,
	transaction,
)};
```

4、提交：交易签名后，提交交易到网络

```
const committedTransaction = await aptos.transaction.submit.simple({
	transacton,
	senderAuthenticator,
});
```

5、等待结果：最后，可以使用`aptos.waitForTransaction`并指定刚刚提交的交易的哈希值来等待交易的结果。

```
const executedTransaction = await aptos.waitForTransaction({ transactionHash: committedTransaction.hash })
```

### 2024.09.09
**学习内容**：安装配置aptos CLI，创建一个项目，熟悉项目结构； <br>
**学习记录**：<br>
Aptos使用Move语言来开发智能合约。

`aptos`命令：Aptos CLI（命令行接口）是一个工具用于帮助编译和测试Move合约。

下载：https://aptos.dev/en/build/cli#-install-the-aptos-cli

```
aptos help // 命令行手册 （检查是否安装成功）
```

创建一个Move package :

```
aptos move init --name <PROJECT_NAME>
```

该命令生成了：`scripts\`、`sources\`、 `tests\` 和`Move.toml`

目录是空的，Move.toml内容如下：

```
[package]
name = "demo"
version = "1.0.0"
authors = []

[addresses]
hello_blockchain = "_"
[dev-addresses]

[dependencies.AptosFramework]
git = "https://github.com/aptos-labs/aptos-core.git"
rev = "mainnet"
subdir = "aptos-move/framework/aptos-framework"

[dev-dependencies]
```

- `name`：package的名字；
- `version`：package的版本；
- `addresses`：描述模块将部署到哪个地址；
- `dependencies`：可能需要使用AptosFramework和其他第三方依赖项；

编写智能合约代码：增加到sources目录。

<!-- Content_END -->
