# 两账号 GitHub 协作 & Devin 换账号迁移 SOP（TOS 长文档）

> 用途：在**已连 `central-memory-safe` 的账号**里，用 `doc_save` 把本文整篇存入 TOS，并写入中央记忆索引。
> 建议 metadata：`{"type":"sop","project":"2026ip"}`；保存后用 `doc_recall` 搜 "换账号迁移 / 团队授权" 验证能命中，必要时 `doc_read` 读全文。

---

## 0. 一句话

用一个 **GitHub 组织 + 团队**承载两账号协作；用一个**控制总仓 devin-control**承载可迁移设置；换账号时「git 拉取 + 接力清单」即可重建。Skills 随 git 自动同步，Knowledge / 中央记忆 / 自定义 MCP 需手动重建。

---

## 1. 账号与角色

- `mykaloooo`：主账号，GitHub 组织 **kaka-media** 的 **owner**。
- `carolfrederic4-arch`：协作账号，组织 **成员(member)**。
- 组织 **kaka-media**：不是登录账号，挂在 mykaloooo 名下；不需要单独邮箱/账号。

## 2. 仓库架构（单仓）

- `kaka-media/2026IP`：唯一主仓（项目 + `.devin/skills/` + `AGENTS.md` + 自动合并 workflow）。
- `kaka-media/devin-control`：控制总仓 / 接力包（`knowledge/`、`playbooks/`、`automations/`、`mcp/`、`integrations.md`、接力清单详细版与一页版、`memory/`）。
- 已废弃：跨账号镜像、`MYKALOOOO_MIRROR_TOKEN`、`two-account-sync` skill。
- `devin/*` 分支经 GitHub Actions 自动合并到 main（用 `GITHUB_TOKEN`，无需外部 token）。

## 3. 团队批量授权

- 组织内团队 **kaka-team**，成员 = mykaloooo(owner) + carolfrederic4-arch(member)。
- `2026IP`、`devin-control` 经团队授权为 **Write**。
- 以后新仓：加进 kaka-team 即自动继承 Write，**不用逐仓加协作者**。
- 验证：`gh api orgs/kaka-media/teams/kaka-team/members`、`gh api repos/kaka-media/<repo>/collaborators/<user>/permission`（应为 write）。

## 4. 权限边界（owner vs member）

| 操作 | member(carolfrederic4-arch) | owner(mykaloooo) |
|---|---|---|
| 读写代码 / 开 PR / 用 Devin 干活 | ✅ | ✅ |
| 装 Devin App / 连组织 / 转仓 / 改组织设置 / 建删团队 | ❌ | ✅ |

> 红条「This action must be performed by an organization owner」= 当前登录的不是 owner，换 mykaloooo 登录。

## 5. Devin GitHub App 安装范围

- 个人账号与组织是**两套独立安装**，都要单独装。
- 迁仓进组织后若 Devin 403，是因为 App 没装到组织：apps/devin-ai-integration → Configure → 选 kaka-media → All repositories → Install。

## 6. 换账号迁移 SOP

> 前提：连组织是 owner 操作，必须 mykaloooo 登录 GitHub；新 Devin 账号已注册。

1. 旧 Devin 账号：Settings → Integrations → GitHub → 对 kaka-media 点 **Disconnect**（只解连接，不动仓库/团队/代码）。
2. 新 Devin 账号：Settings → GitHub → **Connect** → 选 kaka-media → **All repositories** → 由 mykaloooo Install/Approve。
   - 关键：一个 GitHub 组织同时只能挂一个 Devin 账号，所以必须先断旧再连新。
3. Skills：随仓库自动生效，无需操作。
4. Knowledge：新账号说「读 kaka-media/devin-control 的 knowledge/，按 frontmatter 逐条重建 Knowledge Note，_autogen 跳过」。
5. 中央记忆 / 自定义 MCP：手动重连 `central-memory-safe`（地址+鉴权，见 `mcp/central-memory-safe.md`），重连后把 `memory/` 里的短条与本长文档分别 `remember` / `doc_save` 回中央记忆。
6. 验证：新账号能 pull/push 2026IP、能开 PR；4 条 Knowledge 已重建；`recall(projects=["2026ip"])` 能返回记忆。

## 7. 禁止项

- 不把 token/密码/AK/SK 写进代码、Knowledge、Skill、仓库任何文件。
- 不选「Convert user into an organization」（会毁掉个人账号）。
- 不 force push 到 main、不跳过 hooks、不在未确认时删除/覆盖数据。
- 不先断旧账号就硬连新账号（会报 already connected）。
