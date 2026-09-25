# 独立验收

- [ ] Verifier 与 Developer 使用不同模型/provider；无法做到时至少为独立会话和独立上下文
- [ ] Developer 内部 sub-agent、reviewer 或 self-review 结果未被当作独立验收
- [ ] 自动检查的原始结果可复查
- [ ] 适用时实际 API、浏览器或数据库验证
- [ ] 检查错误、边界、日志和敏感信息
- [ ] 记录未验证项目和验证限制
- [ ] 只读验收：未修改代码、测试、Task 或普通文档，仅写 `PROGRESS.md`
- [ ] RC：列出问题、证据和限制，不 commit，返回 Developer
- [ ] PASS：Verifier 本人写入 `PROGRESS.md`，`git add` 本轮全部交付并创建最终任务 commit；不 push、不 merge，除非项目明确授权
