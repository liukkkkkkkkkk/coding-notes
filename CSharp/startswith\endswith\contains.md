# 1.StartsWith 
## 是string类得一个常用方法，用于判断一个字符串是否以指定的字符串开头
## 基础语法：
```c#
public bool StartsWith(string value)
public bool StartsWith(string value, StringComparison(字符串比较) comparisonType（比较类型）)
public bool StartsWith(string value, bool ignoreCase（忽略大小写）, CultureInfo culture（文化信息）)
```
## 常见用法实例
```c#
1.默认区分大小写
string text = "Hello World";
bool result = text.StartsWith("Hello"); // true
bool result2 = text.StartsWith("hello"); // false（区分大小写）
```
```c#
2.忽略大小写比较
string text = "Hello World";
bool result = text.StartsWith("hello", StringComparison.OrdinalIgnoreCase); // true
```
### 注意事项：
1.value不能为null,否则会抛出ArgumentNullException。

2.如果 value 是空字符串 ""，StartsWith 返回 true（因为空字符串是任何字符串的前缀）。

3.推荐在需要忽略大小写时显式指定 StringComparison，避免依赖当前系统区域设置，提高代码可读性和稳定性。
## 安全用法：使用 C# 6+ 的空条件运算符（但 StartsWith 本身不能直接用 ?. 判断 bool）
```c#
bool startsWithABC = input?.StartsWith("ABC") == true;
```
# 2.EndWith
## 判断当前字符串是否以指定的字符串结尾.
## 基础用法：
```c#
bool EndsWith(string value)
bool EndsWith(string value, StringComparison comparisonType)
bool EndsWith(string value, bool ignoreCase, CultureInfo culture)
```
## 常见用法实例：
```c#
string fileName = "report.pdf";

// 区分大小写
bool isPdf = fileName.EndsWith(".pdf");        // true
bool isPDF = fileName.EndsWith(".PDF");        // false

// 忽略大小写
bool isPdfIgnoreCase = fileName.EndsWith(".PDF", StringComparison.OrdinalIgnoreCase); // true
```
# 3.Contains
## 判断当前字符串是否包含指定的子字符串。
## 基础用法：
```c#
bool Contains(string value)
bool Contains(string value, StringComparison comparisonType)
bool Contains(char value)  // 也可以查单个字符
```
## 常见用法实例：
```c#
string message = "Hello World";

bool hasWorld = message.Contains("World"); // true
bool hasworld = message.Contains("world"); // false

// 忽略大小写（.NET Core 2.1+ 支持）
bool hasWorldIgnoreCase = message.Contains("world", StringComparison.OrdinalIgnoreCase); // true
```
## 忽略大小写的例子
```c#
string input = "UserLogin";

if (input.StartsWith("user", StringComparison.OrdinalIgnoreCase))
if (input.EndsWith("LOGIN", StringComparison.OrdinalIgnoreCase))
if (input.Contains("ser", StringComparison.OrdinalIgnoreCase))
{
    // 安全、清晰、跨平台一致
}
```

    


