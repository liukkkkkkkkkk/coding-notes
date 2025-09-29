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
## 3.规范的时间加减函数（支持年、月、日、时、分等单位）：DATEADD(datepart, number, date)
```sql
-- 加 1 个月
SELECT DATEADD(MONTH, 1, GETDATE());

-- 减 2 小时
SELECT DATEADD(HOUR, -2, GETDATE());

-- 加 30 秒
SELECT DATEADD(SECOND, 30, GETDATE());
```
## 4.计算时间差：DATEDIFF(DATEPART,STARTDATE,ENDDATE)
```SQL
-- 计算两个日期的天数差
SELECT DATEDIFF(DAY, '2025-01-01', GETDATE());

-- 计算小时差
SELECT DATEDIFF(HOUR, '2025-09-29 10:00:00', GETDATE());
```
## 5.提取时间部分：DATEPART(DATEPART,DATE)

    返回数字形式的时间部分
```sql
SELECT 
    DATEPART(YEAR, GETDATE()) AS 年,      -- 2025
    DATEPART(MONTH, GETDATE()) AS 月,    -- 9
    DATEPART(DAY, GETDATE()) AS 日,      -- 29
    DATEPART(HOUR, GETDATE()) AS 时,     -- 14
    DATEPART(MINUTE, GETDATE()) AS 分;   -- 30
```
# 常用场景实例
## 1.查询今天的数据
```sql
SELECT * 
FROM 表名 
WHERE 时间列 >= CAST(GETDATE() AS DATE) 
  AND 时间列 < CAST(DATEADD(DAY, 1, GETDATE()) AS DATE);
```
## **2.查询本周的数据**
```sql
SELECT * 
FROM 表名 
WHERE 时间列 >= DATEADD(WEEK, DATEDIFF(WEEK, 0, GETDATE()), 0) -- 本周一零点
  AND 时间列 < DATEADD(WEEK, DATEDIFF(WEEK, 0, GETDATE()) + 1, 0); -- 下周一零点

```

