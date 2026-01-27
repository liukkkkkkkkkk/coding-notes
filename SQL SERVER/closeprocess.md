# SQL SERVER 关闭正在运行的进程
## 首先查看当前所有活动请求及其会话ID
``` sql
-- 示例：查看当前所有活动请求及其会话ID
SELECT session_id, status, command, cpu_time, total_elapsed_time, blocking_session_id
FROM sys.dm_exec_requests
WHERE session_id > 50; -- 通常过滤掉系统进程 (SPID <= 50)

-- 或者查看会话信息
EXEC sp_who2;
```
## 找到目标spid后（假设spid是65），执行KILL指令
```sql
KILL 65;
```
