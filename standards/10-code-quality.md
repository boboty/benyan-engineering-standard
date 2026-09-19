# 代码质量

统一 `make check` 至少运行 `ruff check .`、`pyright`、`pytest`，CI 使用相同门禁。不要依赖 IDE 私有配置。代码更改后检查 diff 与自动检查结果。
