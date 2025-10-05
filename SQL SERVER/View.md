# SQL 视图（view)
## 定义：
视图就是一个保存好的查询语句，你可以给它起个名字，然后像表一样使用它。
## 作用：
**简化复杂查询**
将复杂的 JOIN、GROUP BY、子查询等封装在视图中。

用户只需对视图进行简单的 SELECT 操作，无需了解底层复杂的逻辑。

示例：一个销售报表可能需要连接客户、订单、产品、库存等多个表。创建一个 sales_report_view 视图后，用户只需 SELECT * FROM sales_report_view 即可。

**提高安全性**

可以限制用户访问敏感数据。例如，只允许用户访问包含姓名和部门的视图，而不能直接访问包含薪资的原始员工表。

实现数据的逻辑隔离。

**提供数据的逻辑独立性**

当底层表结构发生变化时（如拆分表、重命名字段），可以通过修改视图定义来保持应用程序不变，只要视图的输出结构不变。

应用程序依赖视图而非直接依赖基表，降低了耦合度。

重用 SQL 逻辑

避免在多个地方重复编写相同的复杂查询语句，提高开发效率和维护性。

## 创建视图语法：
```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

示例：

假设有两个表：

employees (id, name, department_id, salary)
departments (id, dept_name)
我们想创建一个视图，显示员工姓名、部门名称和薪资：

```sql
编辑
CREATE VIEW employee_dept_view AS
SELECT 
    e.name AS employee_name,
    d.dept_name AS department,
    e.salary
FROM employees e
JOIN departments d ON e.department_id = d.id;
```

创建后，就可以像查询表一样查询这个视图：
```sql
SELECT * FROM employee_dept_view WHERE salary > 5000;
```
删除视图
```sql
DROP VIEW view_name;
```



