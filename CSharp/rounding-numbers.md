# C# 保留四位小数的方法

## 问题
如何在 C# 中将浮点数保留四位小数？

## 解决方案

### 方法 1：使用 `Math.Round`
```csharp
double value = 3.1415926;
double rounded = Math.Round(value, 4); // 结果: 3.1416
