# 项目结构

推荐 `app/main.py`、`api/`、`core/`，按需要增加 `schemas/`、`models/`、`services/`、`repositories/`、`db/`。复杂业务可按 API → Service → Repository → Database 组织。无数据库的 Demo 不设 Repository；简单逻辑不强设 Service。Router 不承载大量业务逻辑或复杂 SQL；Repository 不处理 HTTP；Model 不承载完整业务流程。

> 架构层次由实际复杂度决定，而不是由模板决定。
