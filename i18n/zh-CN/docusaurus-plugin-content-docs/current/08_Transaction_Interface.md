---
sidebar_position: 8
title: 8. 交易接口
---

## 交易接口

------------------------------------------------------------------------------------------

#### 转账

<details>
 <summary><code>POST</code> <code><b>chain_sendTransaction</b></code> <code>(转账代币)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | 发送方  |
> | to        |  required | string                  | 接收方  |
> | value     |  required | string (hex)            | 金额  |
> | sliceno   |  required | string (hex)            | 元空间编号  |

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
>    "method": "chain_sendTransaction",
>    "params": [{
>      "from": "0xc3b6472d6370eaf4eb58fff19ce1724c9d61892c",
>      "to": "0x6268af5542c4b0ccbb650a0aaccbfcdfbabf6b52",
>      "value": "0x2E90EDD00",
>      "sliceno": "0x1"
>    }, "", "encryp=none"],
>    "id": "d2c8fe196f9f8d8ace952e9e"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
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

#### 批量转账

<details>
 <summary><code>POST</code> <code><b>chain_airDrop</b></code> <code>(批量转账)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
| allocate  |  required | string                  | 批量转账内容（base64 编码的 JSON 数组）  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_airDrop",
>    "params": ["opcode=token&subcode=airdrop&allocate=[{\"addr\":\"0x...\",\"value\":100}]&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "c52ec4472ccfc12a04c544bf",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x58e4e65d6fa48a79f874e6debe25039405d3702e0d65050ab64146fe8d58d5ee"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 合约交易

<details>
 <summary><code>POST</code> <code><b>chain_sendTransaction</b></code> <code>(执行合约函数)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | 发送方  |
> | to        |  required | string                  | 合约地址  |
> | data      |  required | string (hex)            | 合约调用数据  |
> | sliceno   |  required | string (hex)            | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_sendTransaction",
>    "params": [{
>      "from": "0x2c8e94bbe17cec95f21dfdb55e334cfd4effcd9d",
>      "to": "0x61b3d1759e4d3bd238a2730cb1621fa542a771fd",
>      "data": "0x60086678",
>      "sliceno": "0x1"
>    }, "", "encryp=none"],
>    "id": "a3d18f63c99c7660c87c5f3e"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
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

#### 合约函数代码查询

<details>
 <summary><code>POST</code> <code><b>chain_queryFuntionCode</b></code> <code>(查询函数代码)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | params    |  required | string                  | 函数名称  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**响应字段说明：**
- **info** - 函数代码

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryFuntionCode",
>    "params": ["getTYpe()"],
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
>        "info": "0xae591f49"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
