# 结构体中const使用场景

用const来防止误操作

```cpp
#include<iostream>
#include<string>
using namespace std;

//const 使用场景

struct student{
    string name;
    int age;
    int score;
};

//将函数中的形参改为指针，可以减少内存空间，而不会复制新的副本出来
void printStudents(const student *s){
    //加入const之后，一旦有修改的操作就会报错，可以防止我们的误操作
    //s->age = 100;  操作失败，因为又 const 防止误操作
    cout << "name:" << s->name << " age:" << s->age << " score:" << s->score << endl;
}

int main(){
    //创建结构体变量
    struct student s = {"zhangsan",15,70};

    //通过函数打印结构体变量信息
    printStudents(&s);
    

}
```
