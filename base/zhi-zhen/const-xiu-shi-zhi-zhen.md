# const修饰指针

const修饰指针有三种情况：

1. const 修饰指针 —— 常量指针
2. const 修饰常量 —— 指针常量

### 常量指针

特点：指针的指向可以修改，但是指针指向的值不能修改

```cpp
const int *p = &a;
```

### 指针常量

```cpp
int * const p = &a;
```

特点：指针的指向不可以改，指针指向的值可以改

### 双修饰

```cpp
const int * const p = &a;
```

特点：指针的指向不可以改，指针指向的值不可以改

```cpp
#include<iostream>

using namespace std;

int main(){
    
    // 常量指针
    int a = 10;
    int b = 10;

    const int *p = &a;//指针指向的值不可以改，指针的指向可以改
    // *p=20; 错误
    p = &b;

    //指针常量
    int * const p2 = &a;
    *p2 = 100; //正确
    //p2 = &b 错误，指针的指向不可以改
    
    //双修饰
    const int * const p3 = &a;
    //都不能改
}
```
