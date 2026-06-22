# MCP 重连：central-memory-safe

> ⚠️ MCP 的连接地址 / Token / 鉴权信息**无法通过 git 导出**，也**绝不能**写进本仓库。
> 本文件只记录「这个 MCP 是什么、有哪些工具、怎么用」，连接参数需在新账号后台手动重新填写。

## 这是什么

`central-memory-safe` 是卡卡自建/接入的一个 MCP Server（不在 Devin 官方 MCP Marketplace 列表里，属于自定义 MCP），用于「中央记忆」和「TOS 文档索引」。

## 提供的工具

| 工具 | 用途 |
| --- | --- |
| `recall` | 查询中央记忆（已知项目时必须传 `projects` 参数，如 `["2026ip"]`） |
| `remember` | 新增中央记忆（只新增、不覆盖；metadata 必须含 `type` 和 `project`；角色签名 `role: "aqi"`） |
| `doc_recall` | 搜索 TOS 文档索引（返回 `doc_id`） |
| `doc_read` | 按 `doc_id` 读取 TOS 文档全文 |
| `doc_save` | 保存长文档到 TOS 并写入中央记忆索引 |

## 新账号如何重连（手动，需卡卡操作）

1. 登录新账号后台 → Settings → MCP / Integrations。
2. 添加自定义 MCP Server，名称填 `central-memory-safe`。
3. 填入该 MCP 的服务地址与鉴权（API Key / Token）。
   - 这些值在**老账号后台的 MCP 配置页**，或卡卡自己的服务端记录里。
   - 用 Devin Secret 或后台密钥框填写，**不要**粘进任何仓库文件。
4. 连接成功后，验证：让 Devin 跑一次 `recall(projects=["2026ip"])`，能返回历史记忆即成功。

## 相关 Knowledge

使用规则见 `../knowledge/04_central-memory-safe使用规则.md`（需在新账号重建为 Knowledge Note）。
