---
sidebar_position: 6
title: 6. 内容信息管理
---

## 内容信息管理

------------------------------------------------------------------------------------------

#### 创建地址

<details>
 <summary><code>POST</code> <code><b>chain_address</b></code> <code>(创建类型)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | name      |  required | string                  | 类型名称  |
> | content   |  required | string                  | 类型描述  |
> | sliceno   |  required | int                     | 元空间编号（主元空间编号为 0）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**响应字段说明：**
- **txhash** - 当前交易哈希
- 创建成功后返回对应的地址，需从交易结果查询中获取（contractAddress 字段）。

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_address",
>    "params": ["opcode=Iot&subcode=createaddress&name=soft&content=&sliceno=0", "encryp=none"],
>    "id": "291687c0293354a642e3eadf"
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

#### 更新地址内容

<details>
 <summary><code>POST</code> <code><b>chain_updateContent</b></code> <code>(更新内容)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address   |  required | string                  | 内容地址  |
> | name      |  required | string                  | 内容名称  |
> | content   |  required | string                  | 内容  |
> | sliceno   |  required | int                     | 元空间编号（主元空间编号为 0）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"address":"...","txhash":"..."}`                                  |

**响应字段说明：**
- **txhash** - 当前交易哈希

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_updateContent",
>    "params": ["opcode=Iot&subcode=update&address=&name=&content=&sliceno=0", "encryp=none"],
>    "id": "291687c0293354a642e3eadf"
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
>        "address": "0x2c8e94bbe17cec95f21dfdb55e334cfd4effcd9d",
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
