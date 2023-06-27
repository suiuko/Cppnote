# 初识输入输出

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
