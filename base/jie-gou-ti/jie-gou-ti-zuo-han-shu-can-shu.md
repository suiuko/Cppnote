# 结构体做函数参数

&#x20;作用：将结构体作为参数向函数中传递

传递方式有两种：值传递、地址传递

只有地址传递中的子函数修改形参后，外部的数据也会进行修改。 但是值传递只会修改子函数中的形参，外部不会修改。

```cpp
#include<iostream>
#include<string>
using namespace std;

//定义学生
struct student{
    //姓名
    string name;
    int age;
    int score;
};

//打印学生信息函数
//1.值传递
void printStudent1(struct student s){
    cout << "子函数中 name:" << s.name << " age:" << s.age << " score:" << s.score <<endl;
}

// 2.地址传递
void printStudent2(struct student *p){
    cout << "子函数 2 中 name:" << p->name << " age:" << p->age << " score:" << p->score <<endl;
}

int main(){

    //结构体做函数参数
    //将学生传入到一个参数中，打印学生身上的所有信息

    //创建结构体变量
    struct student s;
    s.name = "zhangsan";
    s.age = 20;
    s.score = 85;

    printStudent1(s);
    printStudent2(&s);
    // cout << "main 函数中打印 name:" << s.name << " age:" << s.age << " score:" << s.score << endl;
    system("pause");
}
```
