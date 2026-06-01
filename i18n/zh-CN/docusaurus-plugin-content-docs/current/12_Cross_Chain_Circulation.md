---
sidebar_position: 12
title: 12. 跨链流通
---

## 跨链流通

------------------------------------------------------------------------------------------

#### 跨链转出

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(将资产转出到另一个元空间)</code></summary>

##### 参数

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address     |  optional | string                  | 合约地址（如为平台资产 TC，参数为空）  |
> | value       |  required | string (hex)            | 转移资产数量  |
> | destsliceno |  required | int                     | 接收资产元空间编号  |
> | sliceno     |  required | int                     | 目标元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 操作结果                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=cross&subcode=transsend&address=&value=0x12&sliceno=10000&destsliceno=199", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 跨链转入

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(接收来自另一个元空间的资产)</code></summary>

##### 参数

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sender      |  required | string                  | 转出方地址  |
> | nonce       |  required | string                  | 转账交易标识  |
> | address     |  optional | string                  | 合约地址（如为平台资产 TC，参数为空）  |
> | value       |  required | string (hex)            | 转移资产数量  |
> | sousliceno  |  required | int                     | 转出交易原始元空间编号  |
> | sliceno     |  required | int                     | 目标元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 操作结果                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=cross&subcode=transrecv&sender=0x...&nonce=&address=&value=0x12&sliceno=10000&sousliceno=199", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------
