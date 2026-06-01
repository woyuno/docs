---
sidebar_position: 15
title: 15. 其他工具
---

## 其他工具

------------------------------------------------------------------------------------------

#### 获取内容 MD5

<details>
 <summary><code>POST</code> <code><b>chain_queryMd5</b></code> <code>(计算 MD5 哈希)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | content   |  optional | string                  | 获取内容的 MD5（base64 编码）  |
> | file1     |  optional | string                  | 获取文件内容的 MD5（完整文件路径）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**响应字段说明：**
- **info** - MD5 哈希字符串

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryMd5",
>    "params": ["opcode=Other&subcode=Md5&content=&file1=", "encryp=none"],
>    "id": "7711b09d8b112406b4492e05"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1208117ccdc1b3975305901b",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "202cb962ac59075b964b0715"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询机器码

<details>
 <summary><code>POST</code> <code><b>chain_queryHardId</b></code> <code>(获取硬件 ID)</code></summary>

##### 参数

> 无

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**响应字段说明：**
- **info** - 机器码字符串

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryHardId",
>    "params": [""],
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
>        "info": "37e4cb5903503f3c6d4f5a88"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
