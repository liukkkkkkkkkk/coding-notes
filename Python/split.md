# split函数（分割函数）
## 当有一个字符串 s="2026-0102-123",想获得0102时 ，应该使用split函数
```python
s = "2026-0102-123"
result = s.split('-')[1]
print(result)  # 输出: 0102
```
## 更安全的写法
```python
s = "2026-0102-123"
parts = s.split('-')
if len(parts) >= 2:
    result = parts[1]
else:
    result = None  # 或者抛出错误、设默认值等
print(result)
```
