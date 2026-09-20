# Fast Track

后端默认 Python 3.12+、FastAPI、Uvicorn、Pydantic v2、pydantic-settings、SQLAlchemy 2.x、Alembic、PostgreSQL、pytest、ruff、pyright。适用于 AI/Agent、内部工具、数据产品、Demo/Prototype、新产品验证、中小型业务系统及没有强制 Java 体系的客户。Web 产品在此后端上叠加[共享前端规范](../standards/15-web-frontend.md)。

Fast Track 不是低质量版本；同样遵守日志、Request ID、错误契约、测试、CI、迁移、独立验收和发布规范。无数据库需求时可以保持轻量，不制造 Service/Repository 空层。

Fast Track WebApp 的默认 Compose 交付包含 app + PostgreSQL，遵循[WebApp Docker Compose 交付基线](../standards/15-web-frontend.md#webapp-docker-compose-交付基线)。纯 API / Agent 项目仍按实际依赖选择服务。
