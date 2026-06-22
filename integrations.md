# Integrations / 集成清单（导出存档）

导出时间：2026-06-22（源账号）

## 原生集成（Native Integrations）

| 集成 | 源账号状态 | 新账号需要做什么 |
| --- | --- | --- |
| GitHub | ✅ 已安装 | 新账号重新授权；确保对 `mykaloooo/2026IP` 和 `mykaloooo/devin-control` 都有读写权限 |
| GitLab / Bitbucket / Azure DevOps | 未安装 | 无需处理 |
| Jira / Linear / Slack / Microsoft Teams | 未安装 | 无需处理 |

## MCP Server

| MCP | 类型 | 说明 |
| --- | --- | --- |
| `central-memory-safe` | 自定义（非 Marketplace） | 必须在新账号手动重连，见 `mcp/central-memory-safe.md` |

> Marketplace 里的其它 MCP（AlloyDB、BigQuery、Asana 等）源账号均未安装，无需处理。

## 密钥 / Secrets

- 源账号 **Devin Secrets 为空**（`list_secrets` 返回 0 条）。
- 单仓方案下**不再需要** GitHub Actions Secret `MYKALOOOO_MIRROR_TOKEN`（镜像已停用，可删除）。
- 两账号协作改为：在 `mykaloooo/2026IP` 把 `carolfrederic4-arch` 加为协作者（无需任何跨仓 Token）。
