# 委托
委托是一种类型，他代表对具有特定参数列表和返回类型的方法的引用
## 可以理解为：**一个“装方法的盒子”**

他的核心作用为3点：

1.装方法：只能装 "签名匹配" 的方法（参数、返回值一致）

2.传方法：可以像变量一样传递这个 "盒子"

3.调方法：通过 "盒子" 间接调用里面的方法

### eg:
```c#
// 定义一个"装无参无返回值方法"的盒子
delegate void MyBox();

// 准备一个符合要求的方法
void SayHi() { Console.WriteLine("Hi"); }

// 用法
MyBox box = new MyBox(SayHi); // 把方法装进盒子
box(); // 调用盒子 → 实际执行SayHi()，输出"Hi"

```
## 系统还提供了现成的盒子：

Action：装无返回值的方法（可带0~16个参数）
```c#
Action action = () => Console.WriteLine("无参数Action");
Action<int, string> action2 = (num, str) => Console.WriteLine($"{num}: {str}");
```

Func：装带返回值的方法（最后一个泛型参数是返回值类型，可带 0~16 个参数）
```c#
Func<int, int, int> addFunc = (a, b) => a + b;
Func<string> getString = () => "Hello, Func";

```

一句话总结：委托让方法能像数据一样被传递和使用，是事件、回调等功能的基础。

