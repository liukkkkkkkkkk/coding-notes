# String.Format ---用于格式化字符串
## 它允许你使用占位符（如 {0}、{1}）将变量插入到字符串模板中。
### 基础用法：
```c#
string result = string.Format("模板字符串", arg0, arg1, ...);
{0} 表示第一个参数（arg0）
{1} 表示第二个参数（arg1）
```
### 示例：
```c#
1.简单字符串格式化
string name = "张三";
int age = 25;
string message = string.Format("姓名：{0}，年龄：{1}", name, age);
// 结果： "姓名：张三，年龄：25"

2.数字格式化
double price = 123.456;
string formatted = string.Format("价格：{0:C}", price);        // 货币格式
// 结果（中文环境）："价格：￥123.46"

string percent = string.Format("完成度：{0:P1}", 0.75);        // 百分比，1位小数
// 结果："完成度：75.0%"

3.日期格式化
DateTime now = DateTime.Now;
string dateStr = string.Format("当前时间：{0:yyyy-MM-dd HH:mm:ss}", now);
// 示例结果："当前时间：2025-10-25 09:45:30"
4.对齐与填充
string s = string.Format("|{0,10}|{1,-10}|", "右对齐", "左对齐");
// 结果： "|    右对齐|左对齐    |"
```
