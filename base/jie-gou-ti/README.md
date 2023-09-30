# 结构体

## 结构体基本概念

结构体属于用户自定义的数据类型，允许用户存储不同的数据类型

## 结构体定义和使用

语法：struct 结构体名 { 结构体成员列表 };

通过结构体创建变量的方式有三种：

* struct 结构体名 变量名
* struct 结构提名 变量名 = {成员 1 值，成员 2 值...}
* 定义结构体时顺便创建变量

```cpp
#include<iostream>
#include <string>
using namespace std;

struct Student{

    //成员列表

    //姓名
    string name;
    //年龄
    int age;
    //分数
    int score;
}s3;



int main(){
//2. 通过学生类型创建具体学生
//2.1 
    struct Student s1;
    //给s1属性赋值，通过.访问结构体变量中的属性
    s1.name = "张三";
    s1.age=18;
    s1.score=100;
    cout << "姓名:" <<s1.name << " 年龄:" << s1.age << " 分数:" << s1.score << endl;
//2.2 struct Student s2={ ... }
    struct Student s2={"李四",19,80};
    cout << "姓名:" <<s2.name << " 年龄:" << s2.age << " 分数:" << s2.score << endl;

//3 在创建结构体的时候 顺便创建结构体变量
    s3.name="wangwu";
    s3.age = 20;
    s3.score = 60;
    cout << "姓名:" <<s3.name << " 年龄:" << s3.age << " 分数:" << s3.score << endl;

}
```
