# 新项目操作 SOP

先选项目入口。模板仓库启用 GitHub Template 后执行其一：

```bash
# API / Agent
gh repo create <owner>/<project> --template boboty/benyan-fastapi-starter --private --clone

# Fast Web
gh repo create <owner>/<project> --template boboty/benyan-webapp-starter --private --clone

# Java Web
gh repo create <owner>/<project> --template boboty/benyan-java-webapp-starter --private --clone
```

1. `cd <project>`，阅读 README 与 AGENTS.md。
2. 修改 AGENTS.md：写清项目目标、阶段、业务边界、特殊规则及偏离默认规范的理由。
3. Web 项目在可用 Docker 环境执行 `docker compose up -d --build`，按 README 给出的 Web 地址验证完整应用；不以宿主机 `make setup` 或 `make dev` 为运行前提。纯 API 项目按其 README 安装。之后再把明确的业务任务交给 Coding Agent。
4. Web 项目交付前，从干净 Compose 环境验证 build、自动 migration、db/app healthy、首页和 `/api/v1/health`，并重启验证数据库 volume 数据仍在。宿主机开发热更新可用 `make setup`、`make dev`。完成后执行 `make check`、`make smoke`；Web 项目再执行 `make e2e`。
5. 每个任务用 Task Card 定义目标、范围、输入、输出、限制与验收标准，并在 Task Board 跟踪状态、依赖、推进策略、当前有效角色及最终验收。任务应能独立执行和验收，且值得完整 Developer → Verifier 流程。检查实际结果、接口/UI、日志、Secret 与 Git diff，交由 Independent Verifier 独立验收；AI self-check 或 Developer 内部 reviewer 不构成独立验收。Verifier 将 PASS/RC/BLOCKED 结论、证据与限制反馈给 Orchestrator 更新 Board；RC 修复后重新启动独立验收。正常流程不维护 `PROGRESS.md`。

纯 API Starter 使用自己的安装命令与 `make check`、`make smoke`；Web Starter 统一提供上述完整命令。
