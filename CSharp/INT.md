# INT 相关讲解
## I.首先先知道int的几个类型(1.int16 2.int32 3.int64)
## II.区别就是大小比较的问题
<img width="800" height="284" alt="image" src="https://github.com/user-attachments/assets/239b963d-2f24-48c9-9bc0-9f4e17def1fc" />

## III.开发过程中怎么选
### 1.普通循环、计数、一般数量：用int
```c#
int count = 0;
for (int i = 0; i < list.Count; i++)
{
    // ...
}
```
### 2.数据库主键、ID、可能超过 21 亿的数：用 long
```c#
long materialId = Convert.ToInt64(material["Id"]);
```
### 3. 范围很小、数量特别多、要省内存：用 short 或 byte  比如状态码、枚举值、很小的计数。但日常业务开发里很少必须用它们。
### 4. 金额不要用 int/long，用 decimal
```c#
decimal price = 19.99m;
```
# 平时写代码，只要不是存数据库主键 ID，闭眼用 int (int32) 就行了；一旦涉及到数据库里的 FID 或者 Id 字段，无脑用 long (int64)，保准不出错。
# 安全万能写法
```c#
// 取长整型/整型，无论底层是 int 还是 long，都不会报错
long id = Convert.ToInt64(material["Id"]); 

// 取字符串，即使为 null 也能安全转为 ""
string name = Convert.ToString(material["Name"]); 
```

