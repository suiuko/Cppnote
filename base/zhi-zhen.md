# 指针

### 指针的基本概念

指针的作用：可以通过指针间接访问内存

* 内存编号是从 0 开始记录的，一般用十六进制数字表示
* 可以利用指针变量保存地址

### 指针变量的定义和使用

```
数据类型 * 变量名;
```

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

int main(){

    //定义指针
    int a = 10;

    //指针定义的语法： 数据类型 * 名字；
    int *p;
    //让指针记录变量地址
    p = &a;
    cout<< "指针为" << p << endl;
    
    //使用
    *p = 1000;
    cout << *p << endl;

}
```
