# 日志与可观测性

生产默认结构化 JSON 日志，至少包含 timestamp、level、service、event、request_id；HTTP 请求包含 method、path、status_code、duration_ms。外部调用记录 provider、operation、duration_ms、result、retry_count。业务上下文通过 logging extra 等方式扩展，不维护固定业务字段表。合法 `X-Request-ID` 优先继承，否则生成；响应和错误体均返回 request_id。严禁记录密码、Token、API key、Authorization、Cookie、完整证件/银行卡号或敏感正文。
