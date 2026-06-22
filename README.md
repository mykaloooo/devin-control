# devin-control — 卡卡 Devin 控制总仓

集中存放卡卡的 Devin Cloud 跨项目配置与**换账号接力包**。换账号时，新账号只需 `git pull` 本仓，再照 **《换账号接力操作流程.md》** 逐步重建即可恢复全套设置。

## 入口

👉 **先读：[`换账号接力操作流程.md`](./换账号接力操作流程.md)** —— 一步步的接力清单。

## 目录结构

```
devin-control/
├── README.md                     # 本文件（总览）
├── 换账号接力操作流程.md           # ★ 接力主清单，从这里开始
├── knowledge/                    # 4 条 Knowledge 正文（需手动重建）
│   ├── 01_卡卡全局协作规则.md
│   ├── 02_阿奇与本叔默认双角色.md
│   ├── 03_圆桌_思想家圆桌_决策圆桌.md
│   ├── 04_central-memory-safe使用规则.md
│   └── _autogen/                 # 系统自动生成，存档用，勿手动重建
│       └── 05_kaka1209仓库索引_autogen.md
├── playbooks/README.md           # 源账号 0 条 Playbook
├── automations/README.md         # 源账号 0 条 Automation
├── mcp/central-memory-safe.md    # MCP 重连说明（不含密钥）
└── integrations.md               # 集成 / Secrets 清单
```

## 仓库架构（2026-06-22 起：单仓 + 组织）

- **唯一主仓 = `kaka-media/2026IP`**（项目内容），归 `kaka-media` 组织所有；另一账号 `carolfrederic4-arch` 通过组织团队成员身份共用（团队批量授权）。
- **本仓 `kaka-media/devin-control`** 只放 Devin 配置 / 接力包，不放项目内容。
- 已弃用早期「双账号镜像」，不再需要 `MYKALOOOO_MIRROR_TOKEN`；仓已迁入 `kaka-media` 组织统一管理。

## 导出快照（2026-06-22）

| 项目 | 数量 | 处理 |
| --- | --- | --- |
| Knowledge Notes | 4 | 手动重建（见 knowledge/） |
| Playbooks | 0 | 无需处理 |
| Automations | 0 | 无需处理 |
| 自定义 MCP | 1（central-memory-safe） | 手动重连 |
| 原生集成 | GitHub | 重新授权 |
| Devin Secrets | 0 | 无需迁移 |

## 安全约定

- 本仓**不含任何 Token / 密码 / API Key / AK·SK**。所有密钥需在新账号后台手动重填。
- 自动生成的 `kaka1209` 索引笔记仅存档，新账号连仓后会自动再生，请勿手动重建。
