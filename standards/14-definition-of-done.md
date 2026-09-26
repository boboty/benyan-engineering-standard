# Definition of Done

交付满足 Task Card 的验收标准，范围与限制清楚；适用的测试、lint、类型检查和接口/UI 验证已执行并报告原始结果、未验证项及原因，检查日志、临时代码、Secret 和必要文档。正式验收前，Orchestrator 确认 Developer 已自检、没有其他可能写入者且交付稳定；验收期间及前后确认交付内容未变化。Independent Verifier 对照 Task Card 审阅完整 diff 和相关代码，沿真实业务链路核对测试路径与证据，评估 mock、手工构造或同源假设是否绕过核心风险，并检查边界遗漏和越界改动；必要时独立运行验证。结论须关联交付版本和实际验证；测试全绿不自动等于完成，未通过或跳过的检查须逐项说明、评估影响，并按 Task 要求判断能否 PASS。PASS 后由 Orchestrator 更新 Task Board；不得以 Developer 自评或口头声称代替独立验收。

> 代码写完不等于完成。模型说完成更不等于完成。
