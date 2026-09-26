# BenYan Engineering Standard

版本：v1.3.1。本仓库是 BenYan Demo、原型与初始产品的通用工程规范权威来源。按需求使用，不要求每个项目拥有所有层。

```text
                   BenYan Engineering Standard
                            │
                Shared Web Frontend Standard
                            │
               ┌────────────┴────────────┐
               │                         │
          Fast Track                Java Track
               │                         │
      FastAPI / Uvicorn          Spring Boot
               │                         │
benyan-webapp-starter     benyan-java-webapp-starter
```

纯 API / Agent / Backend 项目使用 `benyan-fastapi-starter`。快速 Web 产品使用 `benyan-webapp-starter`；已有 Java 体系或明确要求 Java 的 Web 项目使用 `benyan-java-webapp-starter`。两条 Web 路线共享一套前端规范与 API 契约，差别是工程选择，不是质量等级；FastAPI 同样可以用于生产。

通用规范提供默认值。Starter 继承通用规范，具体项目再继承 Starter；项目 `AGENTS.md` 可以显式覆盖通用默认值，冲突时以明确的项目规则为准，偏离须记录工程理由。

从 [原则](standards/00-principles.md)、[共享 Web 前端规范](standards/15-web-frontend.md)和 [Fast Track](profiles/fast-track.md) / [Java Track](profiles/java-track.md) 开始；新项目参见 [操作 SOP](docs/new-project.md)。Task Card、Task Board、Workspace/Git、Agent activity 与独立验收的协作规则见 [AI 协作](standards/12-ai-collaboration.md)。UI 唯一权威来源是本仓库 `design-system/` 内的 BenYan AI Design System。
