# SQL SERVER 时间操作函数

## 1.获取当前时间：GETDATE()
```SQL
SELECT GETDATE(); --例：2025-09-29 14：30：25.123
```
## 2.仅获取日期或时间: CAST
```SQL
-- 获取当前日期（截断时间部分）
SELECT CAST(GETDATE() AS DATE); -- 例：2025-09-29

-- 获取当前时间（截断日期部分）
SELECT CAST(GETDATE() AS TIME); -- 例：14:30:25.1230000
```
