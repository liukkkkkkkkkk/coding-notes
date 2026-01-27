# **SQL数据库连接问题**
## 1.在开发中一般就是左连接或者内连接（在我做的开发过程中）
## 2.**INNER JOIN**
INNER JOIN 可简写为 JOIN：SQL 中 JOIN 默认就是内连接，两种写法效果完全一致；

内连接的本质是 “求交集”—— 只保留多个表中符合连接条件的 “重叠部分” 数据。
可以通过一个生活化的类比理解：
表 A 是 “学生表”，包含 “学生 ID、姓名”；
表 B 是 “成绩表”，包含 “学生 ID、科目、分数”；
连接条件是 “表 A. 学生 ID = 表 B. 学生 ID”；
内连接结果只会保留 “既有学生信息、又有成绩记录” 的学生，没有成绩的学生（表 A 独有的）和没有对应学生的成绩（表 B 独有的）都会被排除。

## 基础语法格式
```sql
SELECT 
    表1.列名1, 表1.列名2, 表2.列名1, 表2.列名2  -- 可指定需要的列，或用 * 表示所有列
FROM 
    表1  -- 主表（顺序不影响内连接结果）
INNER JOIN 
    表2  -- 关联表
ON 
    表1.关联列 = 表2.关联列;  -- 连接条件（通常是两表的主键-外键关系）
```
## 3.右连接 left join 
一般就是确定好on 后边的连接条件即可

左连接的核心特点是完整保留左表的所有记录，同时关联右表中符合条件的记录。

生活化类比：
表 A（左表）是 “员工表”，表 B（右表）是 “部门表”
连接条件是 “员工的部门 ID = 部门表的部门 ID”
左连接结果会包含所有员工（即使没有分配部门），有部门的员工显示对应部门信息，无部门的员工部门信息显示 NULL

##基础语法格式
```sql
SELECT 
    列名1, 列名2, ...  -- 可以指定具体列或使用*
FROM 
    左表  -- 左表的所有记录都会被保留
LEFT JOIN 
    右表
ON 
    左表.关联列 = 右表.关联列;  -- 连接条件
```
## 4.交叉连接 cross join
CROSS JOIN 是 SQL 中的一种表连接方式，它会产生两个或多个表的笛卡尔积（Cartesian Product）。
### 核心特点：
1.无条件匹配：与 INNER JOIN、LEFT JOIN 等需要使用 ON 子句指定连接条件不同，CROSS JOIN 不依赖任何连接条件。

2.笛卡尔积结果：结果集中，第一个表中的每一行都会与第二个表中的每一行进行组合。如果表 A 有 N 行，表 B 有 M 行，那么 CROSS JOIN 的结果将包含 N * M 行。

3.数据量爆炸风险：由于其特性，CROSS JOIN 非常容易产生巨大的结果集，使用时需谨慎
```sql
SELECT 列名列表
FROM table_name_1
CROSS JOIN table_name_2;
-- 注意：SQL 标准中 CROSS JOIN 后面没有 ON 子句
```
# **SQL执行顺序**
## 执行顺序与书写顺序的对比
### 书写顺序
```SQL
 SELECT [DISTINCT] 列名
FROM 表名
[INNER | LEFT | RIGHT] JOIN 表名 ON 连接条件
WHERE 过滤条件
GROUP BY 分组列
HAVING 分组过滤条件
ORDER BY 排序列 [ASC|DESC]
LIMIT 数量;
```
### 执行顺序（实际流程）
```plaintext
1. FROM → 2. ON → 3. JOIN → 4. WHERE → 5. GROUP BY → 6. HAVING → 7. SELECT → 8. DISTINCT → 9. ORDER BY → 10. LIMIT

```
