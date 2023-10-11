# 虚析构和纯虚析构

**多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码**

> 父类指针在析构的时候，不会调用子类中的析构函数，导致子类如果又堆区属性，会造成内存泄露
>
> 虚析构函数和纯虚析构函数只能有一个
>
> 有了纯虚析构之后，这个类也属于抽象类，无法实例化对象。

解决方式：将父类中的析构函数改为**虚析构**或者**纯虚析构**

```cpp
virtual ~Animal(){    //虚析构函数
}

//--------也可以--------

virtual ~Aimal() = 0; //纯虚析构，需要声明也需要实现
//使用纯虚析构需要自己构建函数才可以
Animal::~Animal()
{
	cout << "Animal 纯虚析构函数调用！" << endl;
}

//但是虚析构函数和纯虚析构函数只能有一个

//有了纯虚析构之后，这个类也属于抽象类，无法实例化对象

```

虚析构和纯虚析构共性：

* 可以解决父类指针释放子类对象
* 都需要有具体的函数实现

虚析构和纯虚析构区别：

* 如果是纯虚析构，该类属于抽象类，无法实例化对象

虚析构语法：

`virtual ~类名(){}`

纯虚析构语法：

`virtual ~类名() = 0;`

`类名::~类名(){}`

```cpp
#include<iostream>

using namespace std;

class Animal {
public:

	Animal()
	{
		cout << "Animal 构造函数调用！" << endl;
	}
    //纯虚函数
	virtual void Speak() = 0;

	//析构函数加上virtual关键字，变成虚析构函数
	//virtual ~Animal()
	//{
	//	cout << "Animal虚析构函数调用！" << endl;
	//}

	virtual ~Animal() = 0; //纯析构，需要声明也需要实现
    //有了纯虚析构之后，这个类也属于抽象类，无法实例化对象
};

Animal::~Animal()
{
	cout << "Animal 纯虚析构函数调用！" << endl;
}

//和包含普通纯虚函数的类一样，包含了纯虚析构函数的类也是一个抽象类。不能够被实例化。

class Cat : public Animal {
public:
	Cat(string name)
	{
		cout << "Cat构造函数调用！" << endl;
		m_Name = new string(name);
	}
	virtual void Speak()
	{
		cout << *m_Name <<  "小猫在说话!" << endl;
	}
	~Cat()
	{
		cout << "Cat析构函数调用!" << endl;
		if (this->m_Name != NULL) {
			delete m_Name;
			m_Name = NULL;
		}
	}

public:
	string *m_Name;
};

void test01()
{
	Animal *animal = new Cat("Tom");
	animal->Speak();
    //父类指针在析构的时候，不会调用子类中的析构函数，导致子类如果有堆区属性，会造成内存泄露
	//通过父类指针去释放，会导致子类对象可能清理不干净，造成内存泄漏
	//怎么解决？给基类增加一个虚析构函数
	//虚析构函数就是用来解决通过父类指针释放子类对象
	delete animal;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```
