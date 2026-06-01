---
sidebar_position: 13
title: 13. 跨链元空间
---

## 跨链元空间接口

------------------------------------------------------------------------------------------

#### 登录 VoidChain 获取交易凭证

<details>
 <summary><code>POST</code> <code><b>chain_logonSwap</b></code> <code>(获取交易凭证)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | 账户  |
> | pass      |  required | string                  | 密码  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"mark":"..."}`                                                    |

**响应字段说明：**
- **mark** - 登录成功后返回的交易凭证

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_logonSwap",
>    "params": ["opcode=Account&subcode=Logon&account=wxl_test&pass=12345678", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "cfc6f40fc054a50518da3a54",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "mark": "0b2c7458f88bdbb586884bb9"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 使用交易凭证登录第三方去中心化交易所

由第三方交易所提供接口。

------------------------------------------------------------------------------------------

#### 创建公链私有地址

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(为公链创建本地地址)</code></summary>

**说明：**
由交易所执行，交易所会自动为每个用户在公链上分配一个对应的本地地址，用于从 VoidChain 导入资产的跨链地址。转入转出的创建和维护由交易所负责。此操作影响交易所的资金池。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain     |  required | string                  | 公链 ID（ETH、BSC、TRON 等）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=CreateChainAddr&chain=ETH", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x..."
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询跨链地址

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(查询已创建的跨链地址)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain     |  required | string                  | 公链 ID  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 地址信息                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=QueryChainAddr&chain=ETH", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "0x..."
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### VoidChain 资产跨链转出

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(将 VoidChain 资产转出到公链)</code></summary>

**说明：**
由交易所执行。调用此操作前需先创建公链地址并确保公链地址资金池有足够的资产。发起跨链请求时，资金池会冻结相应数量的资产，然后在公链上释放对应资产。

##### 参数

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain       |  required | string                  | 公链 ID  |
> | coinsymbol  |  required | string                  | 代币符号  |
> | value       |  required | string (hex)            | 金额  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=SwapOut&chain=ETH&coinsymbol=USDT&value=0x12", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x..."
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### VoidChain 资产跨链转入

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(将公链资产转入 VoidChain)</code></summary>

**说明：**
由交易所执行。公链用户将资产转移到交易所地址，交易所确认后调用此方法在 VoidChain 上释放对应资产。

##### 参数

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain       |  required | string                  | 公链 ID  |
> | coinsymbol  |  required | string                  | 代币符号  |
> | address     |  required | string                  | 公链用户地址  |
> | value       |  required | string (hex)            | 金额  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=SwapIn&chain=ETH&coinsymbol=USDT&address=0x...&value=0x12", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x..."
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询 VoidChain 资产

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(查询 VoidChain 上对应资产信息)</code></summary>

##### 参数

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain       |  required | string                  | 公链 ID  |
> | coinsymbol  |  required | string                  | 代币符号  |
> | findaddr    |  optional | string                  | 目标地址（如为空，查询当前账户）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=QuerySpaceCoin&chain=ETH&coinsymbol=USDT&findaddr=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "0000000000000000000000000000000000000000000000000000000000000fff"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询其他链资产

<details>
 <summary><code>POST</code> <code><b>chain_dexSwap</b></code> <code>(查询其他公链上的资产)</code></summary>

**说明：**
对于 VoidChain 以外的公链，需要在配置文件 `data/rpc.host` 中配置相应的 RPC 主机才能正常访问。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | chain     |  required | string                  | 链 ID  |
> | address   |  required | string                  | 代币地址  |
> | findaddr  |  optional | string                  | 目标地址（如为空，查询当前账户）  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_dexSwap",
>    "params": ["opcode=ActiveRobot&subcode=QueryOtherCoin&chain=&address=&findaddr=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "3c0f5890ca10580b4c5b3cab",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "0000000000000000000000000000000000000000000000000000000000000fff"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
