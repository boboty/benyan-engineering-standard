# 数据库与迁移

默认 PostgreSQL 与 SQLAlchemy 2.x。基础字段按需使用 id、created_at、updated_at；仅需要软删除时添加 deleted_at。内部时间统一 UTC，API 使用 ISO 8601。Schema 变更必须有 Alembic migration；禁止生产手工 ALTER TABLE 后不补迁移。
