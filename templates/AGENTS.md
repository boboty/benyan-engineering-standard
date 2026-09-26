# 项目规则模板

先读现有实现；使用本项目技术栈与已定义的质量门禁（若项目提供 `make check` 则使用它）。按业务复杂度建立层次，不创建无意义抽象。存在 UI 时使用 BenYan AI Design System。例外及理由写在本文件。完成后提供实际验证与独立验收证据。

按工程规范《AI 协作》执行：Task Card 定义工作，Task Board 管状态，Workspace/Git 留成果，Agent activity 留过程，Independent Verifier 提供完成证据。由 Orchestrator 维护 Board 和当前有效角色；Developer 实现并自检；Independent Verifier 只读交付并给出 PASS/RC/BLOCKED 结论。正常流程不使用 `PROGRESS.md`。push、merge 须人工授权，除非本文件明确授权。
