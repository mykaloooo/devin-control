---
source: Devin Knowledge Note（导出存档）
original_note_id: note-ead8b0b33dba41daac2199db3f75c7fb
name: central-memory-safe 使用规则
author: user
scope (trigger): when using the central-memory-safe MCP tool to query, store, or manage project memories and documentation
recreate: 新账号需手动重建（见《换账号接力操作流程.md》步骤 A）；同时需先重连 central-memory-safe MCP（见 mcp/central-memory-safe.md）
---

已配置 MCP：central-memory-safe。

用途：
- recall：查询中央记忆
- remember：新增中央记忆
- doc_recall：搜索 TOS 文档索引
- doc_read：读取 TOS 文档全文
- doc_save：保存长文档到 TOS，并写入中央记忆索引

使用原则：
1. 每次处理项目问题前，优先用 recall 查询相关历史记忆。
2. 查文档时先 doc_recall，如果结果里有 doc_id，再用 doc_read 读取全文。
3. 完成重要修复、部署、决策、踩坑后，用 remember 写一条短记忆。
4. 长文档、完整方案、复盘报告用 doc_save，不要塞进 remember。
5. remember 只能新增，不要尝试删除或覆盖历史。
6. 写记忆时 metadata 必须包含 type 和 project。
7. 已知项目时 recall 必须传 projects 参数。
