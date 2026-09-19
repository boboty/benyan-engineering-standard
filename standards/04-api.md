# API

默认前缀 `/api/v1/`，资源使用复数名词。GET 查询、POST 创建或动作、PUT 完整替换、PATCH 局部更新、DELETE 删除。使用 200、201、204、400、401、403、404、409、422、500、503 等合理状态码。成功默认直接返回业务对象；分页返回 `items`、`page`、`page_size`、`total`。不要加入无意义的 `success/code/message/data` 包装。
