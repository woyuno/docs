---
sidebar_position: 7
title: 7. 查询与测试接口
---

## 查询与测试接口

------------------------------------------------------------------------------------------

#### 查询与测试接口

<details>
 <summary><code>POST</code> <code><b>chain_queryTransaction</b></code> <code>(测试交易执行)</code></summary>

**接口用途：**
- 测试交易在单机试运行中执行，根据返回结果决定是否实际向网络提交交易。
- 查询结果操作统一通过试运行接口执行，可立即返回结果，不消耗 Gas 费用。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | 发送方地址  |
> | to        |  required | string                  | 接收方地址  |
> | value     |  required | string (hex)            | 交易金额  |
> | sliceno   |  required | string (hex)            | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"ret_data":"...","err":"..."}`                                    |

**响应字段说明：**
- **ret_data** - 交易执行返回值（十六进制编码）
- **err** - 交易执行返回错误

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryTransaction",
>    "params": [{
>      "from": "0xc3b6472d6370eaf4eb58fff19ce1724c9d61892c",
>      "to": "0x6268af5542c4b0ccbb650a0aaccbfcdfbabf6b52",
>      "value": "0x2E90EDD00",
>      "sliceno": "0x2"
>    }, "", "encryp=none"],
>    "id": "d2c8fe196f9f8d8ace952e9e"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "055169b80c4e2ef96c2b2cbb",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "ret_data": "",
>        "err": ""
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
