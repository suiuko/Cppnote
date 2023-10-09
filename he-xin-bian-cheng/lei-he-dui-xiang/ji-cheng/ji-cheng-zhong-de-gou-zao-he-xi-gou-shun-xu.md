# 继承中的构造和析构顺序

&#x20;子类继承父类后，当创建子类对象，也会调用父类的构造函数

> 创建：先创建父类，再创建子类
>
> 析构：先析构子类，后析构父类

```cpp
#include<iostream>
using namespace std;
class Base 
{
public:
	Base()
	{
		cout << "Base构造函数!" << endl;
	}
	~Base()
	{
		cout << "Base析构函数!" << endl;
	}
};

class Son : public Base
{
public:
	Son()
	{
		cout << "Son构造函数!" << endl;
	}
	~Son()
	{
		cout << "Son析构函数!" << endl;
	}

};


void test01()
{
	//继承中 先调用父类构造函数，再调用子类构造函数，析构顺序与构造相反
	Son s;
}
int main(){
    test01();

}
```

