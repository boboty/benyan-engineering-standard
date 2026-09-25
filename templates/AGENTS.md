# 项目规则模板

先读现有实现；使用本项目技术栈与 `make check`。按业务复杂度建立层次，不创建无意义抽象。存在 UI 时使用 BenYan AI Design System。例外及理由写在本文件。完成后提供实际验证与独立验收证据。

Developer 与 Independent Verifier 的职责、PASS 权限和最终 commit 按工程规范《AI 协作》执行。`PROGRESS.md` 记录任务状态：Developer 可更新进行中/待验收状态，不得写 PASS 或验收结论；Verifier 只能修改 `PROGRESS.md`，PASS 时本人写入结论并创建最终任务 commit。push、merge 须人工授权，除非本文件明确授权。
