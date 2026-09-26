# Changelog

## v1.3.0

- 收敛 AI 协作记录职责：Task 定义工作、Board 管状态、Workspace/Git 留成果、Agent activity 留过程、Verifier 提供完成证据。
- 明确 Orchestrator、Developer、Independent Verifier 的职责，以及 PASS/RC/BLOCKED 和中断接续规则；正常流程移除 `PROGRESS.md` 与最终任务 commit 依赖。
- 补充独立验收证据闭环与任务粒度要求。
- 已有 `PROGRESS.md` 可保留作历史记录；新任务按本版规则执行，无需继续更新；以下 v1.2.0 及更早条目仅为历史记录。

## v1.2.0

- 明确 Developer 与 Independent Verifier 职责：Developer 不得宣布或代写 PASS，内部 reviewer 不构成独立验收。
- PASS 由 Verifier 本人写入 `PROGRESS.md` 并创建最终任务 commit；Verifier 只读交付内容，push / merge 默认人工授权。
- 新增 `templates/PROGRESS.md`，同步 Git 交付、Definition of Done、独立验收清单、AGENTS 模板与新项目 SOP。

## v1.1.0

- 增加唯一共享 Web 前端规范、Fast Track 与 Java Track Profile。
- 明确纯 API、快速 Web、企业 Java Web 的项目入口和新项目 SOP。

## v1.0.0

- 建立工程规范、模板、验收清单并纳入官方 UI Design System 快照。
