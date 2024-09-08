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

# {Elemen}

1. 区块链小白
2. 会一直学习的！

## Notes

<!-- Content_START -->

### 2024.09.07

>https://github.com/aptos-labs/aptos-core/

> github代码参考：https://github.com/aptos-labs/aptos-core/

#### 模块交互与发布

##### 发布

生成账户地址：aptos init

领水：aptos account fund-with-faucet --account de fault 

编译：aptos move compile

测试:  aptos move test

发布：aptos move publish

##### 交互

Aptos 区块链浏览器:https://explorer.aptoslabs.com/

生成的`sender`来搜索（记得切换对应网络）

点击 Modules-run 实施交互，进行基本调试

#### Vector 向量解析

特性：vector 可以理解为其他语言的数组

##### 查询功能

| 语法                                                     | 描述                                    |
| -------------------------------------------------------- | --------------------------------------- |
| vector::is_empty<T>(): bool                              | 查询是否是空数组                        |
| vector::length<T>(v: &vector<T>): u64                    | 查询数组长度                            |
| vector::borrow<T>(v: &vector<T>, i: u64): &T             | 返回数组第n项的数据                     |
| vector::borrow_mut<T>(v: &mut vector<T>, i: u64): &mut T | 返回数组第n项的可变引用                 |
| vector::contains<T>(v: &vector<T>, e: &T): bool          | 如果元素e在数组中，则返回true           |
| vector::index_of<T>(v: &vector<T>, e: &T): (bool, u64)   | 如果元素e在数组中，则返回true和索引位置 |

##### 增删改

| **语法**                                                     | **描述**                    |
| ------------------------------------------------------------ | --------------------------- |
| vector::push_back<T>(v: &mut vector<T>, t: T)                | 添加尾部1个元素             |
| vector::append<T>(v1: &mut vector<T>, v2: vector<T>)         | 添加尾部1个数组             |
| vector::reverse_append<T>(lhs: &mut vector<T>, other: vector<T>) | 添加尾部1个数组，并进行排序 |
| vector::pop_back<T>(v: &mut vector<T>): T                    | 删掉尾部1个元素             |
| vector::destroy_empty<T>(v: vector<T>)                       | 删除数组                    |
| vector::swap<T>(v: &mut vector<T>, i: u64, j: u64)           | 交换数组中两个元素的位置    |
| vector::reverse<T>(v: &mut vector<T>)                        | 反转数组中元素的顺序        |
| vector::insert<T>(v: &mut vector<T>, i: u64, e: T)           | 在长度为i-1处插入一个元素   |
| vector::remove<T>(v: &mut vector<T>, i: u64): T              | 删除索引为i处的元素         |

#### 函数修饰符

##### 核心概念

函数修饰符是用来赋予函数特殊能力的一组关键字。

**主要有以下几类**

可见性

- 无public，私有函数，仅限module内部调用

- friend (public)，模块内部函数，同包模块之间可以调用

- public，模块公开函数，所有模块都可以调用

全局存储引用

- acquires，当需要使用`move_from`、`borrow_global`、`borrow_global_mut` 访问地址下的资源的时候，需要用其修饰

链下

- entry，修饰后，该方法可由链下脚本调用

##### 代码示例1

  ```move
  address 0x42{
      module m{
          friend 0x42::m3;
  
          fun f1() : u64{
              1
          }
          //public 可以被外部访问
          public fun f2() : u64{
              2
          }
          //外部模块无法直接调用，需要声明friend
          public(friend) fun f3() : u64{
              3
          }
      }
      module m2{
          fun f1() : u64{
              0x42::m::f2()
          }
      }
      //view f2 f3
      module m3{
          fun f1() : u64{
              0x42::m::f3()
          }
      }
  }
  ```

##### 代码示例2

  ```move
  module 0x42::Demo{
      use std::debug;
     // 每个账户在 move 中都有一个唯一的 Signer，它通常是账户的创建者或者拥有者。
      use std::signer;
  
      struct Coin has key{
          value:u64
      }
      
  //可以被链下调用
      public entry fun mint(account: &signer, value: u64){
      //将Coin移动到用户的地址中去
          move_to(account, Coin{value});
      }
      
      #[test(account = @0x42)]
      //acquires
      public fun test_mint(account: &signer)acquires Coin{
      
      //获取account的地址
          let addr = signer::address_of(account);
          mint(account, 10);
          
       //从全局资源中借用指定地址addr处的Coin类型资源，并获取其value
          let coin = borrow_global<Coin>(addr).value;
          debug::print(&coin)
      }
  
  }
  ```

#### struct 结构体

##### 核心概念

  Struct 结构体，用来存储具有结构化的数据，sturct可以相互嵌套（不能递归）可存储地址下作为资源，默认情况下，结构声明是线性且短暂的（也就是没办法引用）

    1. 命名必须以大写字母开头
    2. 可以通过has 关键词赋与能力

##### 修饰符

-Copy   值能够被复制
-Drop  值可以在作用域结束时删除
-Key   值可以用作全局存储操作的key，可以索引到相关结构体
-Store   值可以被全局存储，结合key使用，实现嵌套

  除struct类型外，其他的类型默认具备 store,drop,copy 的能力，sturct 最终是存储在用户的地址上（或者被销毁），不存在aptos合约里，aptos合约是一个全纯的函数（相较于Solidity）

##### Object 对象

1. 对象是单个地址的资源容器，用于储存资源；
2. 对象提供了一种集中式资源控制与所有权管理的方法；

##### 创建并转移对象案例

```move
module my_addr::object_playgoud{
	use std::signer;
	use aptos_framework::object::{self,ObjectCore};
	
	entry fun create_and_transfer(caller:&signer,destination:address){
	//接受拥有者地址
	let caller_adsress = signer::address_of(caller);
	//绑定地址和对象
	let constructor_ref = object::create_object(caller_address);
	
	//Set up the object
    
    //transfer to destination
    //转移所有权
    let object = object::object_from_constructor_ref<ObjectCore>(
    &constructor_ref
    );
    object::transfer(caller,object,destination);
	}
	
```



##### 三种对象类型

- 普通对象**。**可删除，且具有随机地址`object::create_object(owner_address: address)`
- 命名对象。不可删除，通过固定的signer和特定的seed生成唯一地址的对象，1个地址只能生成1个，具有确定性地址`object::create_named_object(creator: &signer, seed: vector<u8>)`
- 粘性对象。不可删除，通过signer生成的对象，1个地址可以生成多个，具有随机地址`object::create_sticky_object(owner_address: address)`

示例代码：

```move
module 0x42::demo{
    use std::debug::print;
    use aptos_framework::object;
    use aptos_framework::object::{Object, ConstructorRef, ObjectCore};

    use std::signer;

    const NAME:vector<u8> = b"myObject";
 //can_delet
    public fun createDeleteableObject(caller: &signer):ConstructorRef{
       let caller_addr = signer::address_of(caller);
       let obj = object::create_object(caller_addr);
       obj
    }   


   
    //aptos-labs/examples

//cannt
   public fun createNamedObject(caller: &signer):ConstructorRef{
       let obj = object::create_named_object(caller, NAME);
       obj
    }   
   public fun createStickyObject(caller: &signer):ConstructorRef{
        let caller_addr = signer::address_of(caller);
       let obj = object::create_sticky_object(caller_addr);
       obj
    }   
 #[test(caller = @0x88)]
    fun test2(caller: &signer){
       let obj = createNamedObject(caller);
       print(&obj);
    }


       #[test(caller = @0x88)]
    fun test(caller: &signer){
      let obj = createDeleteableObject(caller);
       print(&obj);
    }

      #[test(caller = @0x88)]
    fun test3(caller: &signer){
      let obj = createStickyObject(caller);
      print(&obj);
    }

}
```



##### Object  配置

一旦您创建了对象，您将收到一个`ConstructorRef`可用于生成其他`Ref`s 。`Refs`可在将来用于启用/禁用/执行某些对象功能，例如传输资源、传输对象本身或删除对象。

1. 允许删除对象 ( `DeleteRef`)

   对于使用默认方法（允许删除）创建的对象，您可以生成一个`DeleteRef`稍后可以使用的对象。这可以帮助消除混乱并获得存储退款。`DeleteRef`您不能为不可删除的对象创建。

2. 一次性转账 ( `LinearTransferRef`)

   此外，如果创建者想要控制所有传输，以提供一次性使用的传输功能。这可用于通过从对象创建者到接收者的一次性传输来创建“灵魂绑定”对象。必须`LinearTransferRef`由对象的所有者使用。

3. 禁用/切换传输 ( `TransferRef`)

   默认情况下，所有对象都是可转让的。这可以通过 来更改，`TransferRef`来生成`object::generate_transfer_ref`。

4. 添加可扩展性（`ExtendRef`)

  将对象变成可动态配置的，可以往里面添置新的 struct 资源。生成一个`ExtendRef`和`object::generate_extend_ref`。此引用可用于为该对象生成签名者。

5. 添加资源

   使用`ConstructorRef`和`object::generate_signer`创建一个签名者，允许您将资源转移到对象上。这使用`move_to`，与将资源添加到帐户的功能相同

### 2024.07.12

<!-- Content_END -->
