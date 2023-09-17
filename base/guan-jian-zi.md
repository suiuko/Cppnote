# 关键字

```cpp
 //std 是名为std的命名空间(namespace)中的
 
 // 标准输入
 std::cin
 std::cin >> v1 >> v2; // 相当于将第一个值存入v1 ,第二个数值存入v2
 // >> 是输入运算符，接受一个 istream 作为左侧的运算对象
 
 //标准输出
 std::cout <<
```

```cpp
#include <iostream>
#include <stdio.h>
using namespace std;

int main(){

    cout << "hello" << endl;
    // std::cout << "hello" << std::endl;

    system("pause");

    return 0;
}
```

### 标准输入输出对象

标准输入：用一个名为 cin 的 sitream 类型的对象

输出： 使用 cout 的 ostream 类型的对象

### 向流写入数据

```cpp
int v1 = 0, v2 = 0;
std::cin >> v1 >> v2;
(std::cin >> v1) >> v2;
```

### 从流读取数据

```cpp
std::cout << "hello" << v1 << "and" << v2
        << "is" << v1 + v2 << std::endl;
```



### 头文件

有标准库中的头文件就用 <> 来包括： `#include <iostream>`&#x20;

如果不属于标准库的头文件，需要用双引号包围 ： `#include "nihao.h"`&#x20;

### 命名空间的using声明

常用到的库函数基本上都属于命名空间std, 例如 std:cin 表示从标准输入中读取内容。

正常情况使用：using namespace std; 就可以
