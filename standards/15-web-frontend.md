# 共享 Web 前端规范

Fast Track 和 Java Track 共用一套前端默认值：Node.js 24 LTS、React 19.x、TypeScript、Vite 8.x、React Router、Vitest、Testing Library、Playwright 与 BenYan AI Design System。需要服务端缓存或 mutation 时引入 TanStack Query。前端始终调用相对路径 `/api/v1/*`，开发时由 Vite proxy 指向后端；不在业务代码写本机后端地址。

状态归属：URL/导航状态用 React Router；服务端数据、缓存和 mutation 用 TanStack Query（出现需求时）；组件局部状态用 `useState`/`useReducer`；跨页面纯客户端状态出现真实需求后才考虑 Zustand 等工具。初始化时不建全局 Store，不把 API 数据复制进全局状态，也不提前引入 Redux、Zustand。

推荐 `web/src/app/` 放启动、Router、Provider；`pages/` 放路由页面；`features/` 放真实业务；`components/` 放复用业务组件；`api/` 放 HTTP client/契约；`hooks/`、`types/`、`styles/` 按需要建立，不为目录图创建空模块。两个 Web Starter 尽量同构；统一 `npm run dev/lint/typecheck/test/build/e2e/check`，其中 `check` 运行前四项中的 lint、typecheck、test、build。

UI 从官方 Design Tokens → 既有组件/规则 → 业务组件 → 页面。必须实际引用 `design-system/styles.css` 和已有组件；页面不得自行发明品牌色、字体、spacing、radius、shadow 或已有组件风格。Design System 快照保持原样，不能在 `web/` 复制另一套 token。

最小 System Status 页面调用 `/api/v1/health`，分别测试加载、成功、失败；Playwright 经真实后端 HTTP 验证页面。API 对外契约与后端语言无关：`/api/v1`、REST 资源、HTTP 状态、分页格式、统一错误体和 `X-Request-ID` 均保持一致。

## WebApp Docker Compose 交付基线

WebApp 默认以 `docker compose up -d --build` 启动完整应用；宿主机只需可用的 Docker 环境，不要求预装 Python、Node 或 PostgreSQL。默认 Compose 必须包含 app 和全部必需依赖，不能只启动数据库。Fast Track WebApp 默认 app + PostgreSQL，不为此基线增加 nginx、Redis 或 Kubernetes。启动完成后 README 指明一个可直接访问完整应用的 Web 地址；前端生产构建和 `/api/v1/*` 由同一应用入口提供。

数据库使用持久化 volume，db 和 app 都有健康检查。迁移在 app 对外 ready 前自动执行；迁移失败时 app 不得 ready。应用使用容器内数据库地址，配置通过环境变量注入，生产凭据遵循[配置与 Secret](07-configuration-secrets.md)。宿主机 `make dev` 可保留用于热更新，但不是项目运行前提。交付时从干净 Compose 环境实际验证构建、迁移、健康状态、首页、API 和重启后的数据持久化。
