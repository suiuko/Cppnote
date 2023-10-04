# 封装

## 封装的意义一

封装是C++面向对象三大特性之一

封装的意义：

* 将**属性和行为**作为一个整体，表现生活中的事物
* 将属性和行为加以权限控制

### **封装意义一：**

在设计类的时候，属性和行为写在一起，表现事物

**语法：** `class 类名{ 访问权限： 属性 / 行为 };`

实例 1：

```cpp
#include<iostream>

using namespace std;

const double PI = 3.14;

//1、封装的意义
//将属性和行为作为一个整体，用来表现生活中的事物

//封装一个圆类，求圆的周长
//class代表设计一个类，后面跟着的是类名

class Circle{
    //访问权限
    //公众权限
public:
    //属性
    int m_r; //半径

    //行为
    //获取园的周长
    double calculateZC(){
        return 2 * PI *m_r;
    }
};


int main(){

    //通过园类，创建园对象
    Circle c1;//c1就是具体的园
    //给园对象的属性进行赋值
    c1.m_r=10;

    cout << "周长:" << c1.calculateZC() << endl;
}
```

实例 2：

类中的属性和行为，统一称为成员

类中的属性：成员属性、成员变量

类中的行为：成员函数、成员方法

```cpp
#include<iostream>

using namespace std;
//设置一个学生嘞，属性有姓名和学号
// 可以给姓名和学号赋值，可以显示学生的姓名和学号

//设计学生类
class Student{
    public://公共权限

    //属性
    string m_Name; //姓名
    int m_Id; //学号

    //行为
    //显示姓名和学号
    void showStudent(){
        cout << "name: " << m_Name << "Id: " << m_Id << endl;
    }

    //给姓名赋值
    void setName(string name){
        m_Name = name;
    }
};

int main(){

    //创建一个具体学生，实例化对象
    Student s1;
    //赋值操作
    s1.m_Name = "zhangsan";
    s1.m_Id = 1;

    //显示学生信息
    s1.showStudent();

    Student s2;
    s2.setName("lisi");
    s2.m_Id = 2;
    s2.showStudent();
}
```

## 封装意义二

类在设计时，可以把属性和行为放在不同的权限吓，加以控制

访问权限有三种：

1. public 公共权限： 成员类内可以访问、类外可以访问
2. protected 保护权限：成员 类内可以访问、类外不可以访问
3. private 私有权限：成员 类内可以访问、类外不可以访问（在继承中和保护有区别）

```cpp
#include<iostream>

using namespace std;

class Person{

    public: 
    //公共权限
    string m_Name; //姓名

    protected:
    //保护权限
    string m_Car;//汽车

    private:
    int m_Password; //银行密码

    public:
    void func(){
        m_Name = "zhangsan";
        m_Car = "zixingche";
        m_Password =1234;
    }
};
int main(){
    Person p1; //实例化具体对象

    p1.m_Name = "lisi";
    // p1.m_Car = "benchi"; //访问不到
    //p.m_Password = 123; //私有权限类外访问不到
}
```
