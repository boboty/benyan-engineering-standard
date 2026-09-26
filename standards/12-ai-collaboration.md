# AI 协作

## 工作记录与任务粒度

协作遵循：**Task 定义工作，Board 管状态，Workspace/Git 留成果，Agent activity 留过程，Verifier 给完成证据。** Agent activity 是工具无关的执行轨迹、会话记录或等价运行记录，不限定特定产品或机制。

- **Task Card** 定义目标、范围、输入、输出、限制和验收标准；任务粒度应能独立执行、独立验收，并值得走完 Developer → Verifier 流程。
- **Task Board** 是推进状态的权威记录，管理状态、依赖、推进策略、当前有效角色和最终验收结果。Task Card 内容与 Board 状态不一致、含义不清或验收标准不可验证时，Orchestrator 暂停相关推进并交由更高层控制角色澄清；不得自行更改 Task 定义。
- **Workspace/Git** 保存可审阅的交付成果及其变更；Agent activity 保存执行过程。完成证据应能从验收结果追溯到交付版本和实际验证，不能以口头声称替代证据。测试全绿不自动等于完成；未通过或跳过的检查须逐项说明、评估影响，并按 Task 要求判断能否 PASS。
- 正常流程不创建或维护 `PROGRESS.md`。仅异常复杂任务在 Task、Board、Workspace/Git 和 Agent activity 都不足以支持恢复时，才可写一次性、可选的 handoff/checkpoint；记录只补足恢复所需上下文，不取代上述权威记录，也不成为后续常规状态文件。

## 角色与 PASS 权限

以下规则与具体工具、模型、产品无关。

- **Orchestrator**：仅在既定 Task Card/Board 范围内安排依赖、推进策略和当前有效角色，并协调 Developer 与 Independent Verifier；不得自行修改 Task 目标、边界或验收标准，不实现交付或自验。凡拆分、合并或重拆涉及 Task 定义变化，或发现产品、架构变化需要裁决时，停止相关工作并交更高层控制角色处理。
- **Developer**：按 Task 与 Board 当前有效分工实现、验证并自检，报告改动、未完成事项、验证结果和限制；不得自行宣布或代写 PASS。内部 reviewer 或 self-review 仅是开发阶段检查，不构成正式独立验收。
- **Independent Verifier**：与 Developer 保持独立判断；由人员执行时应为不同人员，使用 AI 时至少使用独立会话和独立上下文。对照 Task Card 验收标准审阅完整 diff 及相关代码，沿真实业务链路核对测试路径和证据；评估 mock、手工构造、同源假设是否绕过核心风险，并检查边界遗漏和越界改动，必要时独立运行验证。对交付内容只读，不改代码、测试、Task Card 或普通项目文档；将验收结论及证据反馈给 Orchestrator，由其更新 Board。Verifier 不负责实现修复或创建任务 commit。
- **RC**：Verifier 给出具体问题、证据和验证限制；Orchestrator 将任务返回给当前有效 Developer。修复后必须新启动一轮独立 Verifier 验收，不能沿用修复前的 PASS 或验收结论。
- **BLOCKED**：无法按当前 Task、依赖或可用证据继续推进时，说明阻塞原因、已确认事实和所需裁决，由 Orchestrator 在 Board 更新状态；涉及产品、架构或 Task 定义变化，或 Task 定义歧义、验收标准不可验证时，交更高层控制角色裁决。BLOCKED 本身不是完成结论。
- **PASS**：Independent Verifier 确认交付满足 Task Card 验收标准，将本轮结论、可复查证据及限制反馈给 Orchestrator，由 Orchestrator 在 Board 记录最终验收结果。PASS 是针对具体交付版本的证据结论。

正常流程不要求某一角色创建最终任务 commit；按项目 Git 交付规则管理版本。push、merge 默认须人工授权，项目另有明确授权除外。

## Agent 中断与接续

- **轻度中断**：Orchestrator 可指定替代 Developer。接替者先阅读 Task Card、Board、当前 diff/Workspace/Git 和前任 Agent activity，复核可能已变化的运行状态；确认交付边界后只处理剩余工作，并记录接续依据。接替者不是 Verifier，也不继承前任未完成的验收结论。
- 若中断发生在 RC 之后，Board 当前有效角色返回 Developer；修复完成后必须新启动 Independent Verifier。
- **严重中断**：若目标、边界、依赖或运行状态已不可靠，暂停原执行；可在既定 Task 定义内回退或重启。若恢复需要拆分、合并或重拆并改变 Task 定义，须停止并交更高层控制角色裁决。
