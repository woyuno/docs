---
sidebar_position: 14
title: 14. 交易监控
---

## 交易监控

**注意：** 此功能通常由钱包后台程序执行，以避免其他用户操作造成数据混乱。只有本地配置文件 `/etc/listenEvent.conf` 中指定的地址才能操作。

------------------------------------------------------------------------------------------

#### 设置监控

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(注册地址监控)</code></summary>

**说明：**
此操作通常由钱包后台执行，用于注册钱包关注的地址信息。添加账户时同步提交注册的地址信息。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | data      |  required | string                  | 参数说明，将 RegisterEvent 数组序列化为 JSON 后进行 base64 编码  |
> | clear     |  required | boolean                 | 如果为 true，将清除已有配置信息  |

**RegisterEvent 结构：**
```go
type RegisterEvent struct{
  Address   string  `json:"address"`
  Funccode  string  `json:"funccode"`
}
```

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 注册结果                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=registerEvent&data=&clear=false", "encryp=none"],
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
>      "err": ""
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询交易行为

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(查询交易行为)</code></summary>

**说明：**
此操作通常由钱包后台定时执行，用于遍历链上交易数据，记录与当前已注册信息相关的转账信息。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 交易条目数组                                                        |

**响应结构 (TransItem)：**
```go
type TransItem struct {
  From     string  `json:"from"`
  To       string  `json:"to"`
  Funccode string  `json:"funccode"`  // 合约交易函数代码
  Data     string  `json:"data"`      // 合约交易数据
  Amount   uint64  `json:"amount"`    // 平台币数量
  High     uint64  `json:"high"`      // 区块高度
  TxHash   string  `json:"txHash"`    // 交易哈希
}
```

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=scanBlock&sliceno=0", "encryp=none"],
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
>      "content": {}
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 区块链遍历接口

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(遍历区块链)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | begin     |  required | int                     | 起始区块高度，每次最多返回 100 个区块  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 区块数组                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=scanBlock&begin=&sliceno=0","encryp=none"],
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
>      "content": [{
>        "parentHash": "0xcfee308a28697bafef2f635c2c67272a65eab1996c93aebac2bcb29155d5bc77",
>        "miner": "0x6d3da5167929a4b297df09325389d72f35327fa4",
>        "stateRoot": "0x670a4e6f9262854a889e36dd766c6942780a6a9c74840fcbe2a9fde1e4f2c36b",
>        "transactionsRoot": "0xb0ef76de17cce27b75554325e7cba7f22eb3238fb642f35b174c885ae86f1987",
>        "receiptsRoot": "0xbc86b068c10758ec5e644d81b530038b31e6da3450892c7a3dcb6e9a0488c1e8",
>        "Recno": 2,
>        "number": 1,
>        "timestamp": 1742515456744655700,
>        "Txns": [
>          "0xd56f8fd299e309598752d54576395f15d403f2eb274d163e4eaf9e103cf64828"
>        ],
>        "Senders": [
>          "0x35f4646842fc5fe208b7d3fab125c8542be88324"
>        ],
>        "Data": ""
>      }]
>    }
>  }
> ```

**字段说明：**
- **Txns** - 交易哈希数组
- **Senders** - 交易提交者数组
- **Data** - 交易内容（base64 编码）

</details>

------------------------------------------------------------------------------------------
