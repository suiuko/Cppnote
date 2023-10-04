# 函数重载

作用：函数名可以相同，提高复用性

**函数重载满足条件：**

* 同一个作用域下
* 函数名称相同
* 函数参数**类型不同** 或者 **个数不同** 或者 **顺序不同**

> **注意:** 函数的返回值不可以作为函数重载的条件

```cpp
#include<iostream>

using namespace std;

void func()
{
	cout << "func 的调用！" << endl;
}
void func(int a)
{
	cout << "func (int a) 的调用！" << endl;
}
void func(double a)
{
	cout << "func (double a)的调用！" << endl;
}
void func(int a ,double b)
{
	cout << "func (int a ,double b) 的调用！" << endl;
}
void func(double a ,int b)
{
	cout << "func (double a ,int b)的调用！" << endl;
}

//函数返回值不可以作为函数重载条件
//int func(double a, int b)
//{
//	cout << "func (double a ,int b)的调用！" << endl;
//}

int main(){
    func();
	func(10);
	func(3.14);
	func(10,3.14);
	func(3.14 , 10);
}
```

## 注意事项

* 引用作为重载条件
* 函数重载碰到函数默认参数

```cpp
#include<iostream>

using namespace std;
//函数重载注意事项
//1、引用作为重载条件

void func(int &a)
{
	cout << "func (int &a) 调用 " << endl;
}

void func(const int &a)
{
	cout << "func (const int &a) 调用 " << endl;
}


//2、函数重载碰到函数默认参数

void func2(int a, int b = 10)
{
	cout << "func2(int a, int b = 10) 调用" << endl;
}

void func2(int a)
{
	cout << "func2(int a) 调用" << endl;
}

int main() {
	
	int a = 10;
	func(a); //调用无const
	func(10);//调用有const 


	//func2(10); //碰到默认参数产生歧义，需要避免

	system("pause");

	return 0;
}
```
