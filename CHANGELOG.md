# Changelog

## v1.3.1

- 补齐 Agent failover 的真实边界：实践暴露 transport/connection 故障、超时或会话异常不代表旧执行端停止；移交写入权前须先确保前任停止或失去当前 Workspace 写入能力，并始终维持单一有效 Developer。
- 增加异常文件变化时暂停写入、查明并收回多余写入资格、确认 Workspace 稳定后再继续的要求；正式验收前确认 Developer 自检、无其他可能写入者和交付稳定，验收期间保持内容不变。

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
