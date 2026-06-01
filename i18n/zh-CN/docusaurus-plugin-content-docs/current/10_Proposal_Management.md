---
sidebar_position: 10
title: 10. 提案管理
---

## 提案管理接口

------------------------------------------------------------------------------------------

#### TRC100 地址查询

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(查询 TRC100 合约地址)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | TRC100 合约地址                                                     |

**返回投票权和提案提交所需的最低 TC 持有量。**

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=trc100Addr&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "85c42ddbd83c301a0f1bdfc0",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "trc_100_root_addr": "0x2bff1665aef450f0d5a2681f5b2f3a5df00633a0",
>        "trc_100_addr": "0x8d5dd47712a9d4c7ebcb570498a30407fda9a19a",
>        "slice_addr": "0xb2b60dabde3f9acc042528d2665237ac36e23a2e",
>        "lock_addr": "0xeb93cc79834ff35f48d69324476c5c573dc2cdab",
>        "propose_addr": "0x1bd1c092d49548cceb295cf9d0e351c6489fb059",
>        "static_addr": "0x23ee58b0e6cca745a633ae9b4eaa87929b55c803",
>        "cross_addr": "0xc4bb216db77ea104bba866fd535456ce9bd65d2f"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询提案权限

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(查询提案权限)</code></summary>

参与提案会将提案人的信息注册到提案系统中。

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 提案权限信息                                                        |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=queryPermission&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1726b2be8fef1ec6fa30ada2",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "addr": "0x35f4646842fc5fe208b7d3fab125c8542be88324",
>        "balance": 100000000000,
>        "trc100": 0,
>        "allowPropose": false,
>        "allowVote": false
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 提交提案

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(提交提案)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | 提案类型（0-5）  |
> | content   |  required | string                  | 提案内容  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=addPropose&type=0&content=&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1726b2be8fef1ec6fa30ada2",
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

#### 投票

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(投票)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | 提案类型（0-5）  |
> | agree     |  required | int                     | 0 - 同意，1 - 反对  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=vote&type=0&agree=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 移除提案

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(移除提案)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | 提案类型（0-5）  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=removePropose&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询投票信息

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(查询投票结果)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | 提案类型（0-5）  |
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 投票统计                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=queryVote&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### 响应示例

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1726b2be8fef1ec6fa30ada2",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "Pass": 1,
>        "Disagree": 0,
>        "PassTC": 523843176,
>        "DisagreeTC": 0
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
