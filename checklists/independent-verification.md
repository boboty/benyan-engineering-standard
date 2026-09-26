# 独立验收

- [ ] Verifier 与 Developer 保持独立判断；由人员执行时为不同人员，使用 AI 时至少为独立会话和独立上下文
- [ ] 正式启动前，Orchestrator 已确认 Developer 完成自检、没有其他可能写入者，且交付稳定
- [ ] 验收前后已用 Git diff、Workspace 状态、文件摘要或等价方式确认交付内容未变化；如 Verifier 发现变化，暂停验收并反馈 Orchestrator，旧交付验收结论失效；变化后的交付稳定后新启动独立验收
- [ ] Developer 内部 reviewer 或 self-review 结果未被当作独立验收
- [ ] 逐项对照 Task Card 验收标准；阅读完整 diff、相关代码和测试证据，必要时独立运行验证
- [ ] 自动检查的原始结果可复查
- [ ] 适用时实际 API、浏览器或数据库验证
- [ ] 审阅真实业务链路和测试路径；评估 mock、手工构造和同源假设是否绕过核心风险
- [ ] 检查遗漏边界、错误、日志、敏感信息及超出 Task Card 范围的 diff
- [ ] 记录未验证项目和验证限制
- [ ] 只读验收：未修改交付内容、Task Card、Task Board 或普通项目文档
- [ ] 结论与证据指向明确的交付版本；测试全绿不自动等于完成，未通过或跳过的检查须逐项说明、评估影响，并按 Task 要求判断能否 PASS
- [ ] RC：列出问题、证据和限制；Orchestrator 将任务返回当前有效 Developer，修复后新启动独立验收
- [ ] PASS：Verifier 将结论、证据和限制反馈给 Orchestrator，由其更新 Task Board
- [ ] BLOCKED：说明阻塞、已确认事实和待裁决事项，由 Orchestrator 更新 Board 并确定下一步
