---
sidebar_position: 5
title: 5. 主网节点管理
---

## 主网节点管理

------------------------------------------------------------------------------------------

#### 配置管理密码

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(设置管理密码)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | pass      |  required | string                  | 原始密码  |
> | newpass   |  required | string                  | 新密码  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 成功消息                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["updateTmac","op=setpass&pass=&newpass=123","encryp=none"],
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
>      "content": "setpass successful"
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 退出真空网络

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(退出真空网络以进行远程维护)</code></summary>

退出真空网络后，可通过 SSH 对主网节点进行远程维护。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | pass      |  required | string                  | 密码  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 成功消息                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["updateTmac","op=stop&pass=123","encryp=none"],
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
>      "content": "StopMac Successful! and Maintain through SSH connection"
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
