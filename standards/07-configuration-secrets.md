# 配置与 Secret

使用 pydantic-settings、环境变量和 `.env.example`。分别考虑 local、test、staging、production；环境变量覆盖本地配置。真实密码、Token 和生产数据库凭据不得进入 Git。示例值只能用于本地开发。Production 不得静默使用开发默认配置；关键配置缺失时应 fail fast。
