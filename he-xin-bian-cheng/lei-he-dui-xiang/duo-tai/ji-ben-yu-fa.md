# 基本语法

## 基本概念

多态分为两类

* 静态多态: 函数重载 和 运算符重载属于静态多态，复用函数名
* 动态多态: 派生类和虚函数实现运行时多态

静态多态和动态多态区别：

* 静态多态的函数地址早绑定 - 编译阶段确定函数地址
* 动态多态的函数地址晚绑定 - 运行阶段确定函数地址

> 如果不用虚函数，则继承的时候 函数已经早绑定，所以调用子类继承方法的时候会执行父类的方法，不会执行子类的方法。这样就会导致错误。但是 将父类函数改变为虚函数后就不会产生这种情况。
>
> 我们希望传入什么对象，那么就调用什么对象的函数
>
> 如果函数地址在编译阶段就能确定，那么静态联编\
> 如果函数地址在运行阶段才能确定，那么动态联编

### 动态多态满足条件：

1. 有继承关系
2. 子类重写父类中的虚函数

### 动态多态使用

父类指针或引用指向子类对象：&#x20;

```cpp
void doSpeak(Aniaml &animal){ //Animal &animal = cat;
    animal.speak();
}

```

## 总结：

多态满足条件

* 有继承关系
* 子类重写父类中的虚函数

多态使用条件

* 父类指针或引用指向子类对象

重写：函数返回值类型 函数名 参数列表 完全一致称为重写

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>
using namespace std;

class Animal
{
public:
	//Speak函数就是虚函数
	//函数前面加上virtual关键字，变成虚函数，那么编译器在编译的时候就不能确定函数调用了。
	virtual void speak()
	{
		cout << "动物在说话" << endl;
	}
};

class Cat :public Animal
{
public:
	void speak()
	{
		cout << "小猫在说话" << endl;
	}
};

class Dog :public Animal
{
public:

	void speak()
	{
		cout << "小狗在说话" << endl;
	}

};
//我们希望传入什么对象，那么就调用什么对象的函数
//如果函数地址在编译阶段就能确定，那么静态联编
//如果函数地址在运行阶段才能确定，就是动态联编

void DoSpeak(Animal & animal)
{
	animal.speak();
}
//
//多态满足条件： 
//1、有继承关系
//2、子类重写父类中的虚函数
//多态使用：
//父类指针或引用指向子类对象

void test01()
{
	Cat cat;
	DoSpeak(cat);


	Dog dog;
	DoSpeak(dog);
}
int main(){
    test01();

}
```
