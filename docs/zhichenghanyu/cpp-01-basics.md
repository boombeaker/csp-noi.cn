- CSP-J
- 数学思维
- C++ 语法
- 数据结构、算法
- 工具：考试环境 Linux

## 复习

### 程序的基本结构

回顾一下，以下是最简单的 C++ 程序：

```cpp
#include <iostream>

int main(int argc, char* argv[]) {
    std::cout << "Hello, world!" << std::endl;
    return 0;
}
```

实际上，它的每一行，都蕴藏深刻的原理。
我们要逐一分析。

**头文件**

`#include <iostream>` 从语法角度看：所谓导入接口。比如 `std::cout` 和 `std::endl` 是在 `<iostream>` 头文件（真的就是一个文件，而已）。

从原理角度看：它其实是“找到文件，并复制粘贴文件内容”。

**main的参数和返回值**
main 函数的标准形式是这样的：`int main(int argc, char* argv[])`
是不是很好奇，`main` 为什么会有需要有参数和返回值呢？

其实，main 函数是整个程序的入口和出口。命令行可以通过参数和返回值，和 `main` 互动。

实际上，在 windows 下，我们写的 `cpp` 源文件代码，最终会变成 `exe` 可执行文件。

经过以下代码实验：

```cpp
#include <iostream>
using namespace std;
int main(int argc, char* argv[]) {
    std::cout << argc << std::endl;

    return 0;
}
```

我们知道了，`main` 的参数和返回值，其实都是命令行可以进行交互的。
一般的系统会约定，一个程序如果 **正常** 退出，那么应该返回 `0`。

## 新课数组

```cpp
int main(int argc, char* argv[]) {
    double score01 = 80;
    double score02 = 80;
    double score03 = 100;
    double score04 = 50;
    //...

    return 0;
}
```

有时候，如上，我们可能有一组 **类型相同** 的数据。
如果我们一个个定义变量，那么代码会很长，而且不好维护。

比如，在以上基础上，如果需要计算平均分，那么就需要：

```cpp
int main(int argc, char* argv[]) {
    double score01 = 80;
    double score02 = 80;
    double score03 = 100;
    double score04 = 50;
    
    double sum = (score01 + score02 + score03 + score04) / 4;
    return 0;
}
```

为了缓解这种矛盾，C 语言中，提供了 **数组** 这种概念。用于定义一组 **类型相同** 的数据。

**数组定义**
我们已经知道，普通数据类型的定义语法：

```cpp
type 变量名
```

数组的定义：

```cpp
type 数组名[数组长度]
```

我们用数组，简单修改以上的代码：

```cpp
#include <iostream>
using namespace std;
int main(int argc, char* argv[]) {
    double scores[4];
    scores[0] = 80;
    scores[1] = 80;
    scores[2] = 100;
    scores[3] = 50;
    
    double sum = (scores[0] + scores[1] + scores[2] + scores[3]) / 4;
    return 0;
}
```

**数组的引用**
定义完数组后，使用`数组名[下标]`，就可以引用数组中的元素了。
注意：C 语言中，数组的下标是从 `0` 开始的。

知道如何引用数组后，我们利用循环，可以进一步简化代码：

```cpp
#include <iostream>
using namespace std;
int main(int argc, char* argv[]) {
    double scores[4];
    scores[0] = 80;
    scores[1] = 80;
    scores[2] = 100;
    scores[3] = 50;
    
    double sum = 0;
    for (int i = 0; i < 4; i++)
    {
        sum = sum + scores[i];
    }
    sum = sum / 4;
    return 0;
}
```

其实，如果学习了如果批量初始化数组，以上代码可以继续简化：

```cpp
int main(int argc, char* argv[]) {
    double scores[4] = { 80, 80, 100, 50 };
    
    double sum = 0;
    for (int i = 0; i < 4; i++)
    {
        sum = sum + scores[i];
    }
    sum = sum / 4;
    return 0;
}
```

详细的语法和原理，是我们下次的内容。

## 作业

1. 根据今天数组的内容，写一个程序，它的输入有2行：
第1行代表成绩的数目
第2行代表具体的成绩，中间以空格分隔

比如：
```text
4
80 80 100 50
```

要求的输出：输出这些成绩的平均分。
比如以上输入，应该输出：

```text
77.5
```
