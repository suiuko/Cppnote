# 静态成员

静态成员就是在成员变量和成员函数前加上关键字static，称为静态成员

静态成员分为：

* 静态成员变量
  * 所有对象共享同一份数据
  * 在编译阶段分配内存
  * 类内声明，类外初始化
* 静态成员函数
  * 所有对象共享同一个函数
  * 静态成员函数只能访问静态成员变量

## 静态成员

### 静态变量两种访问方式

> 注意：静态变量也有访问权限

#### 1. 通过对象

```cpp
//1、通过对象
    Person p1;
    p1.m_A = 100;
    cout << p1.m_A << endl;
```

#### 2. 通过类名

```cpp
cout << "m_A = " << Person::m_A << endl;
```

### 类外初始化操作

在类中定义后，在外面定义全局，格式为： 类::参数 = 数值；

```cpp
class Person{
    public:
    //1. 所有对象都共享同一份数据
    //2. 编译阶段就分配内存
    //3. 类内声明，类外初始化操作

    static int m_A;
};
int Person::m_A = 100; //类外初始化操作
```

```cpp
#include<iostream>

using namespace std;

//静态成员变量
class Person{
    public:
    //静态对象特点：
    //1. 所有对象都共享同一份数据
    //2. 编译阶段就分配内存
    //3. 类内声明，类外初始化操作

    static int m_A;

    private:
	static int m_B; //静态成员变量也是有访问权限的

   
};
int Person::m_A = 100;
int Person::m_B = 10;

void test01(){

    Person p;
    cout << p.m_A << endl;

    Person p2;
    p2.m_A = 200; //更改后 数值会发生改变

    cout << p.m_A << endl;
}

void test02(){
    //静态成员变量 不属于某个对象上，所有对象都共享同一份数据
    //因此静态成员变量有两种访问方式

    //1、通过对象
    Person p1;
    p1.m_A = 100;
    cout << p1.m_A << endl;

    //2、通过类名
    cout << "m_A = " << Person::m_A << endl;

    //私有静态变量访问不到！
    //cout << "m_B = " << Person::m_B << endl; //私有权限访问不到
}
int main(){
    // test01();

}
```

## 静态成员函数

> 静态成员函数不可以访问非静态成员，无法区分到底是哪个对象的

```cpp
#include<iostream>

using namespace std;

//静态成员函数
class Person
{

public:

	//静态成员函数特点：
	//1 程序共享一个函数
	//2 静态成员函数只能访问静态成员变量
	
	static void func() //静态成员函数
	{
		cout << "static void func调用" << endl;
		m_A = 100; //静态成员函数可以访问静态成员变量
		//m_B = 100; //错误，不可以访问非静态成员变量
	}

	static int m_A; //静态成员变量
	int m_B; // 
private:

	//静态成员函数也是有访问权限的
	static void func2()
	{
		cout << "func2调用" << endl;
	}
};
int Person::m_A = 10;


void test01()
{
	//静态成员变量两种访问方式

	//1、通过对象
	Person p1;
	p1.func();

	//2、通过类名
	Person::func();


	//Person::func2(); //私有权限访问不到
}


int main(){

    test01();
}
```
