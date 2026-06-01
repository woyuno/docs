---
sidebar_position: 9
title: 9. 钱包锁定接口
---

## 钱包锁定接口

------------------------------------------------------------------------------------------

#### 锁定钱包

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(锁定钱包)</code></summary>

钱包锁定是钱包所有者的自主操作，承诺收到的代币将按照锁定规则释放。
不可重复锁定。如果已锁定，锁定按钮应置灰。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | nums      |  required | int                     | 代币数量  |
> | begin     |  required | int                     | 开始日期  |
> | days      |  required | int                     | 锁定天数  |
> | type      |  required | int                     | 锁定类型（0 - 每日释放，1 - 到期释放）  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**响应字段说明：**
- **txhash** - 交易哈希

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=lock&nums=123&begin=12345678&days=1&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "aa80aa0c6bb0c7d81ac7e5b3",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询锁定信息

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询钱包锁定信息)</code></summary>

钱包锁定是钱包所有者的自主操作，承诺收到的代币将按照锁定规则释放。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | addr      |  required | string                  | 查询对应地址的锁定信息  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 锁定详情                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=querylock&addr=0x...&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "Addr": "0x35f4646842fc5fe208b7d3fab125c8542be88324",
>        "Nums": 10000000000,
>        "Begin": 1711036800,
>        "Days": 48,
>        "LType": 0
>      }
>    }
>  }
> ```

**字段说明：**
- **Addr** - 锁定地址
- **Nums** - 数量（除以 9 个零，保留 2 位小数）
- **Begin** - 开始日期
- **Days** - 天数（UI 可计算结束日期）
- **LType** - 类型（0 - 线性释放，1 - 到期释放）

</details>

------------------------------------------------------------------------------------------

#### 解锁

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(解锁钱包)</code></summary>

只能在到期后才能执行解锁。
提交解锁前：必须检查是否已到期，否则直接返回解锁失败信息。
如果未到期，解锁按钮应置灰。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | 无        |  N/A      | N/A                     | 无需参数  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**响应字段说明：**
- **txhash** - 交易哈希

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=unlock", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "aa80aa0c6bb0c7d81ac7e5b3",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
