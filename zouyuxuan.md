---
timezone: Asia/Shanghai
---


# {zouyuxuan}

1. 我叫邹宇轩，5年开发经验，掌握go，rust，cairo，move开发语言
2. 不逼自己一把怎么能坚持下来

## Notes

<!-- Content_START -->

### 2024.09.07
#### 1、阅读aptos官方文档，了解object使用方法，阅读aptos源代码，了解object在智能合约中如何使用
#### 2、编译aptos智能合约，部署测试上网络

笔记内容

### 2024.09.08
#### aptos client 使用
#### 1、创建账户 aptos init --profile 
```
# 创建一个tz账户
aptos init --profile tz 
aptos 会在当前文件夹目录下创建一个.aptos隐藏文件夹，文件内容包括账户名称，公钥，私钥等信息

# 领水 address 制定为自己的账户
1、aptos account fund-with-faucet --profile tz 
2、curl -X POST
'https://faucet.devnet.aptoslabs.com/mint?amount=10000&address=0xd0f523c9e73e6f3d68c16ae883a9febc616e484c4998a72d8899a1009e5a89d6'

# 查看tz账户余额，使用--url参数指定环境
aptos account balance --account tz --url https://fullnode.devnet.aptoslabs.com

# 使用tz账户给0x9002a65796acd991b7f0bca4bc7e6428821fa393ba95ba356cf7769435d12250 转账
aptos account transfer --account 0x9002a65796acd991b7f0bca4bc7e6428821fa393ba95ba356cf7769435d12250 --amount 1000 --profile tz

```

### 2024.09.09
#### 熟悉move语言基本语法，编写基础智能合约
### 2024.09.10
#### 创建move合约，编译部署
```
1、初始化一个名为game的智能合约项目文件
aptos move init --name game
2、编译智能合约
aptos move compile
```
`注意事项：` 如果编译过程中may take a little while to download git dependencies...下载依赖报错
替换 [dependencies.AptosFramework]中git地址为 "https://gitee.com/WGB5445/aptos-core.git"
### 2024.09.11
#### 阅读aptos move example源码
### 2024.09.12
### 2024.09.13
### 2024.09.14
### 2024.09.15
### 2024.09.16
### 2024.09.17
### 2024.09.18
<!-- Content_END -->