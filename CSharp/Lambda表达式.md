#  Lambda表达式（匿名函数）
## Lambda 表达式本质上是一个可传递的代码块，你可以像传递参数一样将它传递给方法。它常用于 LINQ 查询、事件处理、异步编程、集合操作等场景。
1.基本语法形式：
```c#
(input parameters) => expression
```
**1.1** => 是 lambda 运算符，读作“goes to”。

**1.2**左边是输入参数（可以有零个、一个或多个）。

**1.3**右边是表达式或语句块。
## 基本语法实例
1.简单表达式
```c#
// 定义一个 lambda：接收 x，返回 x 的平方
x => x * x;

// 使用示例：Find 委托查找偶数
int[] numbers = { 1, 2, 3, 4, 5 };
var even = Array.Find(numbers, x => x % 2 == 0); // 返回 2

```
**Array 是 C# 中所有数组类型的基类（根类），它是一个静态类，位于 System 命名空间中。
你可以把它理解为 “数组的工具箱” —— 它提供了一系列静态方法，用于操作各种类型的数组（如 int[]、string[]、double[] 等)**
详细解释
1. Array 是一个类，不是关键字
虽然我们写数组时用 int[] 这样的语法，但底层所有数组都继承自 System.Array 类。
Array 类本身不能被实例化（不能 new Array()），但它提供了很多静态方法来操作数组。
2. Array.Find() 是一个静态方法
Array.Find<T>(T[] array, Predicate<T> match) 是 Array 类提供的一个泛型静态方法。
它的作用是：在数组中查找第一个满足条件的元素。

2.多个参数（用括号包围）
```c#
// 接收两个参数，返回它们的和
(x, y) => x + y;
```
3.无参数
```c#
() => Console.WriteLine("Hello");
```
4.语句块（使用大括号）
```c#
x => 
{
    if (x > 0) return "正数";
    else return "非正数";
};
```
## 常见应用场景
1. LINQ查询（最常用）
```c#
   var people = new List<Person>
{
    new Person { Name = "Alice", Age = 25 },
    new Person { Name = "Bob", Age = 30 }
};
// 使用 lambda 筛选年龄大于 25 的人
var adults = people.Where(p => p.Age > 25);
// 排序
var sorted = people.OrderBy(p => p.Name);
// 选择特定字段
var names = people.Select(p => p.Name);
 ```
2.委托(Action和Func)

C# 提供了内置的泛型委托类型来配合 lambda：

Action<T>：不返回值

Func<T, TResult>：有返回值
```c#
// Action 示例：无返回值
Action<string> greet = name => Console.WriteLine($"Hello, {name}!");
greet("Tom"); // 输出: Hello, Tom!

// Func 示例：有返回值
Func<int, int, int> add = (x, y) => x + y;
int result = add(3, 5); // result = 8
```
