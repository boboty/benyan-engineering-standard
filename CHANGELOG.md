# Changelog

## v1.3.5

- 明确 Git 交付边界：Independent Verifier PASS 前不创建正式 implementation commit；Developer 实现、自检与 RC 修复保持在同一稳定 Workspace 中，由 Verifier 验收完整 diff。
- 明确 Task 是交付边界、RC 不是版本边界；PASS 后再一次性形成最终 implementation commit，并由 Orchestrator 记录 accepted commit/baseline。
- 仅在真实跨会话、跨机器或长时间中断恢复风险下允许 checkpoint commit，且不得替代最终通过验收的正式交付。

## v1.3.4

- 将执行平台与研发协议解耦：Orca、Paseo 等 harness 仅属于运行时上下文，不进入 Task / Board / Gate 等协议状态。
- Orchestrator 只使用当前 Run 明确指定的 execution backend；未指定时停止在调度准备状态，不根据历史示例或仓库记录自行推断平台。
- 明确平台、模型、effort 与运行模式均为可替换资源，角色合法性来自职责边界与独立性。

## v1.3.3

- 统一 PostgreSQL 主版本基线为 16，并要求开发、测试、CI、Compose 与交付环境保持主版本一致。
- Fast Track 与 Java Track 显式采用 PostgreSQL 16；禁止使用 `postgres:latest`。
- 项目若因既有验证或兼容约束使用 PostgreSQL 17，须在项目规则中明确说明并保持全链路版本一致。

## v1.3.2

- 收敛 Task Board 粒度：Board 只持久化跨会话仍有调度价值的阶段状态、依赖、推进策略、阻塞/决策点和最终验收结果；RC、Verifier 轮次、当前 Agent 身份等短期执行态默认由 Orchestrator 会话维护。
- 推荐 Board 使用 `READY / IN PROGRESS / BLOCKED / DONE`，需要人工裁决 Gate 时增加 `DECISION REQUIRED`；正式验收与 RC 修复通常属于 `IN PROGRESS` 内部过程。
- 明确 Harness 设计原则：优先约束权力边界、不可逆风险和验收结果，不因假设模型会犯错而预先堆叠细粒度状态与操作规则；实践中反复出现的错误再补具体约束。

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
