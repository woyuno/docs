---
sidebar_position: 3
title: 3. 公共查询
---

## 公共查询

```json
{
  "jsonrpc": "3.0",
  "method": "chain_queryInfo",
  "params": ["{key}","{content}","encryp=none"],
  "id": "1"
}
```

**参数说明：**
- `pubTrustQuery` - 信任机器公共信息查询
- `pubChainQuery` - 主网公共信息查询

公共信息查询无需登录。

------------------------------------------------------------------------------------------

#### 获取边缘信任机器 ID

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询当前边缘信任机器 ID)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | edgeInfo - 查询边缘信任机器 ID，用于添加到真空网络节点白名单  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"ret":"0","err":"","content":{"edge_id":"..."}}`                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=edgeInfo","encryp=none"],
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
>        "edge_id": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 节点入口信息查询

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询对应真空网络节点入口信息)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | edgeInfo - 查询边缘信任机器 ID，用于添加到真空网络节点白名单  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Entry information                                                   |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=entry","encryp=none"],
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
>        "edge_id": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c",
>        "entry": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 真空网络状态查询

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询真空网络运行状态)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | edgeInfo - 查询边缘信任机器 ID，用于添加到真空网络节点白名单  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Vacuum network status                                               |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=network","encryp=none"],
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
>        "edge_id": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c",
>        "Network": "running"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 获取平台账户信息

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询账户信息)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address   |  required | string                  | Account address  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Account information                                                 |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryAccount&address=0x...&sliceno=0","encryp=none"],
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
>        "root": "0x1d550f3d3c7a9e1536a524938cba",
>        "Balance": 10000000000000000,
>        "Owner": "0x35f4646842fc5fe208b7d3fab125c8542be88324",
>        "Grant": "0x0000000000000000000000000000000000000000",
>        "GasValue": 0,
>        "GasBuyValue": 0,
>        "Nonce": 13,
>        "CodeHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
>        "Content": "test"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询交易结果

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(查询交易结果)</code></summary>

**注意：** 任何返回 `txhash` 字段的操作都表示是一个链上更新操作。需要每秒查询操作结果，直到返回结果，以完成接口提交流程。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | hash      |  required | string                  | 交易哈希  |
> | sliceno   |  required | int                     | 元空间编号（主元空间编号为 0）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 交易详情                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryTx&hash=0xf8af2a6966c3......&sliceno=0","encryp=none"],
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
>        "root": "0d233ef6a3ddfacdf46",
>        "status": 2,
>        "transactionHash": "0x414f5206c1bc79",
>        "contractAddress": "0x000000000000000",
>        "blockHash": "0x0e09ff036fad9e67da6a4b",
>        "blockNumber": 35,
>        "transactionIndex": 1,
>        "return_data": "",
>        "from": "0x000000000000000000000000000",
>        "to": "0xb880e69da1e4bfa1e4bbbbe5889be5",
>        "nonce": 0,
>        "txtype": 2,
>        "tx_content": "01fe01fe01fe01f",
>        "amount": 0,
>        "timeval": 43
>      }]
>    }
>  }
> ```

**交易状态：**
- `0` - 交易仍在交易池中
- `1` - 交易已打包，等待确认
- `2` - 已确认并返回执行结果
- `3` - 交易失败并已删除

**交易类型：**
- `0x1` - 普通活动
- `0x2` - 转账活动
- `0x3` - 设备活动（隐藏，稍后发布）
- `0x4` - 内容活动
- `0x5` - 平台活动

</details>

------------------------------------------------------------------------------------------
