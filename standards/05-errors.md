# 错误

错误响应为 `{"error":{"code":"TASK_NOT_FOUND","message":"Task not found","request_id":"req_xxx"}}`，必要时加入 `details`。HTTP 状态表示类别，`code` 供程序判断，`message` 供人理解，`request_id` 供排查。客户端不得收到堆栈、SQL、文件路径、Secret、Token、内部服务地址。
