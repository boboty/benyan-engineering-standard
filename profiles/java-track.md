# Java Track

默认 Azul Zulu Java 25 LTS、Spring Boot 4.1.x、Spring Web MVC、Spring Validation、Spring Data JPA、PostgreSQL、Flyway、Gradle Wrapper、JUnit 5、Spring Boot Test、Testcontainers、Actuator；Web 前端遵循[共享规范](../standards/15-web-frontend.md)。客户明确要求 Java 21 时，项目 `AGENTS.md` 可说明理由并覆盖默认版本，不强迫现有客户升级。构建和 CI 使用 Azul Zulu，不使用其他 JDK 发行版或 Maven。

适用于已有 Java/Spring 体系、大型企业客户、长期维护系统、复杂事务、大量企业集成、较强团队协作要求或明确 Java 技术栈要求。推荐 `config/`、`web/`、`domain/`、`service/`、`repository/`、`infrastructure/`，只创建实际需要的代码；禁止为了目录图建立 BaseController、BaseService、BaseRepository、CommonManager 或万能 Utils。

用 OncePerRequestFilter 与 MDC 传递 Request ID，用 `@RestControllerAdvice` 输出 BenYan 错误契约；生产日志使用 Spring Boot 内建结构化 JSON。数据库对象 snake_case、时间 UTC、Schema 变更入 Flyway；没有真实业务表时不造假模型。Testcontainers 只在数据库行为需验证时使用。架构复杂度由真实问题驱动。
