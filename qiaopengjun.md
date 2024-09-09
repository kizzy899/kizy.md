---
timezone: Asia/Shanghai # 北京时间 (UTC+8)
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
    Qiao Pengjun 乔鹏军。有Python、Go、Rust、solidity的开发经验。大约是去年开始了解Web3，最近在学习solidity。对区块链技术很感兴趣。了解了一点Solana、Sui、Starknet... 正在继续学习。希望本次学习能让我更深入的了解Web3。拥抱Web3，拥抱未来。
2. 你认为你会完成本次残酷学习吗？
   我认为我会完成本次残酷学习，因为我有信心，并且我相信我能够克服任何困难。

## Notes

<!-- Content_START -->

### 2024.09.07

Aptos 区块链上的每个账户都由一个 32 字节的账户地址标识。
与其他区块链中账户和地址隐式不同，Aptos 上的账户是显式的，需要先创建才能执行交易。
可以通过将 Aptos 代币 (APT) 转移到 Aptos 来显式或隐式创建账户。

Aptos 上有三种类型的账户：

标准账户——这是一个典型的账户，对应一个地址和一对相应的公钥/私钥。
资源账户- 一个没有对应私钥的自主账户，供开发者存储资源或上链发布模块。
对象- 存储在代表单个实体的单个地址内的一组复杂资源。

帐户地址为 32 字节。它们通常显示为 64 个十六进制字符，每个十六进制字符为一个半字节。有时地址以 0x 为前缀。
Aptos区块链默认采用Ed25519签名交易。

Aptos 区块链存储三种类型的数据：

交易：交易表示区块链上的账户正在执行的预期操作（例如转移资产）。
状态：（区块链账本）状态代表交易执行输出的累积，即存储在所有资源内的价值。
事件：交易执​​行时发布的辅助数据。
只有交易才能改变账本状态。

<https://aptos.dev/en/build/get-started/developer-setup>

Install the Aptos CLI on Mac

```bash
brew update
brew install aptos

aptos help

brew update
brew upgrade aptos

intensive-colearning-aptos on  main via 🅒 base took 4.3s 
➜ aptos --version              
aptos 4.1.0


Code/Aptos/hello_aptos via 🅒 base
➜
aptos init
Configuring for profile default
Choose network from [devnet, testnet, mainnet, local, custom | defaults to devnet]
devnet
Enter your private key as a hex literal (0x...) [Current: None | No input: Generate new key (or keep one if present)]

No key given, generating key...
Account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 doesn't exist, creating it and funding it with 100000000 Octas
Account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 funded successfully

---
Aptos CLI is now set up for account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35 as profile default!
 See the account here: https://explorer.aptoslabs.com/account/0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35?network=devnet
 Run `aptos --help` for more information about commands
{
  "Result": "Success"
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 1m 32.7s
➜
aptos account list
{
  "Result": [
    {
      "0x1::account::Account": {
        "authentication_key": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
        "coin_register_events": {
          "counter": "0",
          "guid": {
            "id": {
              "addr": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
              "creation_num": "0"
            }
          }
        },
        "guid_creation_num": "2",
        "key_rotation_events": {
          "counter": "0",
          "guid": {
            "id": {
              "addr": "0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35",
              "creation_num": "1"
            }
          }
        },
        "rotation_capability_offer": {
          "for": {
            "vec": []
          }
        },
        "sequence_number": "0",
        "signer_capability_offer": {
          "for": {
            "vec": []
          }
        }
      }
    }
  ]
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 2.5s
➜
aptos account fund-with-faucet --account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35
{
  "Result": "Added 100000000 Octas to account 0xee6c038b66df7ed8aa91eb700938003ce29647f402c090ededd89b87a3c70e35"
}
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base took 2.8s
➜
touch StudyAptosNotes.md
                                                                                                                                              

Code/Aptos/hello_aptos via 🅒 base
➜
open -a Typora StudyAptosNotes.md
                                                                                                                                              


Code/Aptos/hello_aptos via 🅒 base
➜
ls
StudyAptosNotes.md assets

Code/Aptos/hello_aptos via 🅒 base
➜
ls -a
.                  ..                 .aptos             StudyAptosNotes.md assets

Code/Aptos/hello_aptos via 🅒 base
➜
cd .aptos/

Aptos/hello_aptos/.aptos via 🅒 base
➜
ls
config.yaml

Aptos/hello_aptos/.aptos via 🅒 base
➜
c
```

<https://aptos.dev/en/build/cli/install-cli/install-cli-mac>
<https://www.youtube.com/watch?v=_EFoVYcrbiY>
<https://plugins.jetbrains.com/plugin/14721-move-on-aptos>
<https://move-developers-dao.gitbook.io/aptos-move-by-example>
<https://marketplace.visualstudio.com/items?itemName=movingco.move-analyzer-plus>
<https://www.youtube.com/watch?v=87eeYsstBD4>

### 2024.09.08

[idea 配置 aptos](https://docs.pontem.network/02.-move-language/intellij_ide_extension)

创建项目

```bash
mkdir hello_optos
cd hello_aptos
```

初始化项目

```bash
aptos move init --name hello_aptos
```

初始化账户

```shell
aptos init
```

编译

```shell
aptos move compile
```

测试

```shell
aptos move test
```

部署

```shell
aptos move publish --named-address hello_aptos
➜ aptos move publish --named-addresses my_addrx=3b551727cac1bd5dc45023b869c9e37dd9e1830fc02ffe32f19597a668ba906d
```

运行

```shell
aptos move run --function-id 0x1::hello_aptos::greet --args "hello"
```

### 2024.09.09

笔记内容

### 2024.09.10

笔记内容

### 2024.09.11

笔记内容

### 2024.09.12

笔记内容

### 2024.09.13

笔记内容

### 2024.09.14

笔记内容

### 2024.09.15

笔记内容

### 2024.09.16

笔记内容

### 2024.09.17

笔记内容

### 2024.09.18

笔记内容

### 2024.09.19

笔记内容

### 2024.09.20

笔记内容

### 2024.09.21

笔记内容

### 2024.09.22

笔记内容

### 2024.09.23

笔记内容

### 2024.09.24

笔记内容

### 2024.09.25

笔记内容

### 2024.09.26

笔记内容

### 2024.09.27

笔记内容

### 2024.09.28

笔记内容

### 2024.09.29

笔记内容

### 2024.09.30

笔记内容

### 2024.10.01

笔记内容

### 2024.10.02

笔记内容

### 2024.10.03

笔记内容

### 2024.10.04

笔记内容

### 2024.10.05

笔记内容

### 2024.10.06

笔记内容

### 2024.10.07

笔记内容

### 2024.10.08

笔记内容

### 2024.10.09

笔记内容

<!-- Content_END -->
