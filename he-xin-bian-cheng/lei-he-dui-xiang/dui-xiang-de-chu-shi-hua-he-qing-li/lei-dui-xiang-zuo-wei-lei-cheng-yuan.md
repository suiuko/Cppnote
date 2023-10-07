# 类对象作为类成员

&#x20;类中的成员可以是领一个类的对象，我们称该成员为对象成员

```cpp
class A{ }
class B {
    A a;
}
```

> 在Person类中，声明phone m\_phone； 然后进行初始化赋值的时候 传参为：string pName；这时编译器会使用隐式转换法来进行赋值。
>
> 当其他类对象作为本类成员，构造时候先构造类对象，在构造本身
>
> 析构的时候顺序和构造的顺序相反，先析构本身，再析构别的。

```cpp
#include<iostream>
#include<string>

using namespace std;

//类对象作为类成员

//手机类
class Phone{
    public:
        Phone(string pName){
            m_PName = pName;
            cout << "Phone构造" << endl;
        }

        ~Phone()
	    {
		cout << "Phone析构" << endl;
	    }


    //手机品牌名称
    string m_PName;
};

//人类
class Person{
    public:
    //Phone m_phone = pName; 隐式转换法
    Person(string name, string pName):m_Name(name),m_Phone(pName){
        // m_Name = name;
        cout << "Person构造" << endl;
    }
    ~Person()
	{
		cout << "Person析构" << endl;
	}
    
    //姓名
    string m_Name;
    //手机
    Phone m_Phone;
};

void test01(){
    Person p("san","iphone");

    cout << p.m_Name << "拿着" << p.m_Phone.m_PName << endl;
}

int main(){ 
    test01();
    return 0;
}
```
