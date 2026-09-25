# AI 协作

任务至少说明目标、边界、输入、输出、验收标准、不可修改范围。一句话可以启动任务，不能定义完成。大范围修改前读 AGENTS.md 和现有代码并明确计划。完成后运行测试、lint、类型检查，报告变更、未完成事项和证据。AI self-check 不等于独立验收。

## 角色与 PASS 权限

以下规则与具体工具、模型、产品无关。

- **Developer**：负责实现、测试、普通文档修改和 self-check；不得自行宣布 PASS，不得代写 PASS，不执行最终任务 commit。Developer 自行启动的 sub-agent、内置 reviewer、self-review 或其他内部 reviewer 只属于开发阶段内部检查，不构成正式独立验收。
- **Independent Verifier**：作为独立验收角色执行验收。优先使用与 Developer 不同的模型/provider；无法做到时至少使用独立会话和独立上下文。对交付内容只读：不改业务代码、测试、Task 和普通项目文档，不顺手修复问题；唯一可修改的项目状态文件是 `PROGRESS.md`。
- **RC**：Verifier 给出具体问题、证据和验证限制，不 commit，返回 Developer 修复。
- **PASS**：Verifier 本人把 PASS 及独立验收证据和限制写入 `PROGRESS.md`，对本轮全部交付执行 `git add`，并创建最终任务 commit。该 commit 同时包含 Developer 的交付内容和 Verifier 写入的验收状态。

PASS 是独立验收角色的判断权、状态写入权和对所接受版本的 commit 权；Verifier 口头 PASS 后由 Developer 代写状态或代为提交，不构成 PASS。push、merge 默认须人工授权，项目另有明确授权除外。
