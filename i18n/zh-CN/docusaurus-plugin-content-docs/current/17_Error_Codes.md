---
sidebar_position: 17
title: 17. 错误码
---

## 错误码

| 代码 | 消息 | 说明 |
|------|------|------|
| 1000 | Unrecognized error | 无法识别的错误 |
| 1001 | Timeout | 请求超时 |
| 1002 | Param format fail | 请求参数格式错误 |
| 1003 | Session not found! | 会话未找到 |
| 1004 | Function Disabled | 功能已禁用 |
| 1005 | The user has not logged in yet! | 尚未登录 |
| 1006 | Parameter format error | 请求参数格式错误 |
| 1007 | The data is too long to exceed 1024 | 数据过长，超过 1024 |
| 1008 | Error parsing encrypted file! | 解析加密文件错误 |
| 1009 | Session lost! | 会话丢失 |
| 1010 | Decrypt error! | 解密错误 |
| 1011 | Find account addr error! | 查找账户地址错误 |
| 1012 | The trust has not been registered | 信任未注册 |
| 1013 | Find Rec Fail! | 记录查找失败 |
| 1014 | Rec count is 0 | 记录数为 0 |
| 1015 | Json parse error | JSON 解析错误 |

------------------------------------------------------------------------------------------

## 注意事项

- VoidChain 平台代币最多可保留 9 位小数，因此在转账和管理代币时，需要在末尾添加 9 个零。
- 平台每天给每个账户约 10 次免费 Gas 费用，但这不是自动的。每个账户需要每天主动执行一次免费能量领取。
- 在平台上操作时，每次 Gas 费用会先从赠送池中扣除。如果耗尽，会自动购买一个平台币的 Gas 能量。当前定价也约为 10 次操作。购买的 Gas 能量将保持有效，不会被清零，但赠送的能量将在次日自动清零。
