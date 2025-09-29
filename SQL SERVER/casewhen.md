# case when 语句
首先他是一个条件表达式，它的功能类似于编程语言中的 if-else 或 switch-case 语句。
## 1.CASE WHEN 主要用于：

数据转换：将数值、代码等转换为更具可读性的文本。

分组统计：在 GROUP BY 或聚合函数中创建自定义分组。

条件计算：根据条件对数据进行不同的计算。

处理空值或异常值：为特定情况提供默认值或特殊处理。

生成报表：创建更直观的报告输出
## 2.基础语法
  ### 2.1 简单 CASE 表达式（Simple CASE）  将一个表达式与多个可能的值进行比较。
```sql
CASE expression
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ...
    ELSE default_result
END
```
  ### 2.2  搜索 CASE 表达式（Searched CASE）—— 更常用且灵活 ,对每个 WHEN 子句评估一个布尔条件。

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE default_result
END
```
## 3.eg:
假设我们有一个名为 students 的表，包含字段：name, score, gender, age。

成绩等级划分（搜索 CASE）
```sql

SELECT 
    name,
    score,
    CASE 
        WHEN score >= 90 THEN 'A'
        WHEN score >= 80 THEN 'B'
        WHEN score >= 70 THEN 'C'
        WHEN score >= 60 THEN 'D'
        ELSE 'F'
    END AS grade
FROM students;
```

示例 ：年龄分组统计（结合 GROUP BY）
```sql
编辑
SELECT
    CASE 
        WHEN age < 18 THEN 'Under 18'
        WHEN age BETWEEN 18 AND 30 THEN '18-30'
        WHEN age BETWEEN 31 AND 50 THEN '31-50'
        ELSE 'Over 50'
    END AS age_group,
    COUNT(*) AS count
FROM students
GROUP BY 
    CASE 
        WHEN age < 18 THEN 'Under 18'
        WHEN age BETWEEN 18 AND 30 THEN '18-30'
        WHEN age BETWEEN 31 AND 50 THEN '31-50'
        ELSE 'Over 50'
    END;
```
输出：按年龄段分组统计人数。

示例 ：条件计算（奖金计算）
```sql
SELECT 
    name,
    score,
    salary,
    CASE 
        WHEN score > 95 THEN salary * 0.2
        WHEN score > 90 THEN salary * 0.1
        ELSE 0
    END AS bonus
FROM employees;
```
输出：根据绩效分数计算奖金。
