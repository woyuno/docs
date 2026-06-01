---
sidebar_position: 11
title: 11. 静态元空间
---

## 静态元空间

------------------------------------------------------------------------------------------

#### 申请静态元空间

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(申请静态元空间)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | 元空间编号（0 为主元空间）  |

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
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=applyStaticSlice&sliceno=0", "encryp=none"],
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

#### 获取元空间创世块

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(获取创世块内容)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | 元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 创世块信息                                                          |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=getGenesisBlock&sliceno=0", "encryp=none"],
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
>        "block_number": 0,
>        "block_hash": "0x..."
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 添加节点

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(添加节点)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | file1     |  required | string                  | 完整路径，文档中每行保存一个节点信息  |
> | sliceno   |  required | int                     | 目标元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 操作结果                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=addnodes&file1=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 删除节点

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(删除节点)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | file1     |  required | string                  | 完整路径，文档中每行保存一个节点信息  |
> | begin     |  required | int                     | 起始位置  |
> | len       |  required | int                     | 条目数量  |
> | sliceno   |  required | int                     | 目标元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 操作结果                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=delnodes&file1=&begin=&len=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### 查询节点

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(查询节点信息)</code></summary>

##### 参数

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | begin     |  required | int                     | 起始序号  |
> | len       |  required | int                     | 条目数量  |
> | sliceno   |  required | int                     | 目标元空间编号  |

##### 响应

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | 节点列表                                                            |

##### 示例 cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=nodeinfo&begin=&len=&sliceno=10001", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------
