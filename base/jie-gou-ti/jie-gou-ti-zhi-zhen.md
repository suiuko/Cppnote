# 结构体指针

作用： 通过指针访问结构体中的成员

利用操作符 -> 可以通过结构体指针访问结构体属性

```cpp
#include<iostream>

using namespace std;

struct student{
    string name;
    int age;
    int score;
};

int main(){
    //创建学生结构体变量
    struct student s={"zhangsan",18,100};
    //通过指针指向结构体变量
    struct student *p = &s;
    //通过指针访问结构体变量中的数据
    cout << "name:" << p -> name <<  " age:" << p->age << " score:" << p->score <<endl;

}
```
