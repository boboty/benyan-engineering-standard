# Git 与交付

建议 main、feature/*、fix/*、refactor/* 分支。提交使用 `feat:`、`fix:`、`refactor:`、`test:`、`docs:`、`chore:`，保持小而完整。避免 `update`、`fix bug` 等含糊信息。

一个任务对应一个最终任务 commit，由 Independent Verifier 在 PASS 后创建，包含本轮全部交付与 `PROGRESS.md` 中的验收状态；Developer 不执行最终任务 commit，RC 时不 commit（见 [AI 协作](12-ai-collaboration.md)）。push、merge 默认须人工授权，项目另有明确授权除外。
