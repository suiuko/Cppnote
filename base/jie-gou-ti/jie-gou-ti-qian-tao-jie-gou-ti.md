# 结构体嵌套结构体

&#x20;作用：结构体中的成员可以是另一个结构体

例如：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体

```cpp
#include<iostream>
#include<string>
using namespace std;

struct student
{
    /* data */
    string name;
    int age;
    int score;
};

struct teacher
{
    /* data */
    //成员列表
    int id; //职工编号
    string name; //教室姓名
    int age;
    struct student stu;//子结构体 学生
};


int main(){
    //创建老师
    teacher t;
    t.id = 10000;
    t.name = "laowang";
    t.age = 50;
    t.stu.name = "xiaowang";
    t.stu.age = 18;
    t.stu.score = 60;
    cout << "teacher name" << t.name << " t.id" <<t.id
    <<" teacher age" << t.age << " S name" << t.stu.name << " S age" << t.stu.age
    << " S score" << t.stu.score << endl;

}
```
