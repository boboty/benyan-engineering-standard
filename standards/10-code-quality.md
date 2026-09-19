# 代码质量

统一 `make check` 至少运行 `ruff check .`、`pyright`、`pytest`；它是代码级门禁。适用时另设 smoke/integration 命令，实际启动应用并从 HTTP 边界验证；CI 同时执行两类检查。不要依赖 IDE 私有配置。代码更改后检查 diff 与自动检查结果。
