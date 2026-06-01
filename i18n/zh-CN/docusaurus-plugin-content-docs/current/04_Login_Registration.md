---
sidebar_position: 4
title: 4. 登录与注册
---

## 登录与注册

**请求格式说明：**
- **D_Encryption** - 加密方式：rsa、pass、none。登录成功前使用 rsa 加密，登录成功后使用 pass 加密。
- **特别说明：** 如需浏览器支持，需要在本地启动 https 服务器代理，通过代理访问本地信任机器接口，前端可以使用 none 模式进行无加密通信。
- **D_Session** - 首次连接返回的会话 ID。后续所有通信都必须包含此 ID，以识别为同一连接。
- **注意：** 文档中所有以 "D_" 开头后跟下划线的关键字均为已定义的关键字，需要替换为相应的定义，后续不再逐一说明。

------------------------------------------------------------------------------------------

#### 获取会话 ID

<details>
 <summary><code>POST</code> <code><b>chain_getKey</b></code> <code>(获取加密公钥)</code></summary>

##### 参数

> 无

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"session":"...","pubkey":"..."}`                                  |

**响应字段说明：**
- **Session** - 后续连接的会话 ID
- **pubkey** - 服务器为当前连接分配的通信公钥

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_getKey",
>    "params": [],
>    "id": 1
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": 1,
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "session": "5cbb9dab5678e998670e9e61",
>        "pubkey": "q\r\nHQIDAQAB\r\n"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 注册

<details>
 <summary><code>POST</code> <code><b>chain_register</b></code> <code>(注册账户)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | 账户名  |
> | password  |  required | string                  | 密码  |
> | refer     |  optional | string                  | 推荐人地址  |
> | invitenonce | optional | string                | 邀请码  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**响应字段说明：**
- **txhash** - 当前交易哈希
- 注册结果需要从交易结果查询中获取

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_register",
>    "params": ["opcode=Account&subcode=Add&account=&password=&refer=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "a1aa68e1666efb46a61e2cd2",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x5c0407caf8df3ae28202e068b6f97025f69852688afce09de11f8283fbb7dd48"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 登录

<details>
 <summary><code>POST</code> <code><b>chain_logon</b></code> <code>(账户登录)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | 账户名  |
> | password  |  required | string                  | 密码  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**响应字段说明：**
- **info** - Base64 加密的账户地址信息

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_logon",
>    "params": ["opcode=Account&subcode=Logon&account=&password=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "2ec689ba8b07f98ed9e6b504",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "eyJhZGRy......"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 导出助记词

<details>
 <summary><code>POST</code> <code><b>chain_exportKeystore</b></code> <code>(导出助记词)</code></summary>

##### 参数

> 无

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**响应字段说明：**
- **info** - Base64 加密的助记词内容

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_exportKeystore",
>    "params": ["opcode=Account&subcode=exportMnem", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "2ec689ba8b07f98ed9e6b504",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "cGxlYXNlIGF0aGxldGUgaGVhdnkgYXVndXN0IHRydXRoIHJvYXN0IG1pcmFjbGUgc3Ryb25nIGVsYm93IGRpc21pc3Mgc3BlbGwgY2hpY2tlbg=="
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 登出

<details>
 <summary><code>POST</code> <code><b>chain_logout</b></code> <code>(登出)</code></summary>

##### 参数

> 无

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 成功确认                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_logout",
>    "params": ["opcode=Account&subcode=Logout", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "2ec689ba8b07f98ed9e6b504",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": ""
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
