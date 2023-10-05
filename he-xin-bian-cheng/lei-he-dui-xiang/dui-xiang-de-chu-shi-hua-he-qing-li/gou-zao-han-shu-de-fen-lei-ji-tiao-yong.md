# 构造函数的分类及调用

## 两种分类方式：

按参数分为： 有参构造和无参构造

按类型分为： 普通构造和拷贝构造

## 三种调用方式：

> 调用默认构造函数的时候，不要加()；这样会让编译器认为是一个函数的声明，不会认为在创建对象
>
> 不要利用拷贝构造函数，初始化匿名对象；编译器会认为 Person(p3) 等价于Person p3;对象声明会触发重定义；

### 括号法

```cpp

Person p; //调用无参构造函数
Person p2(10); //有参构造函数
Person p3(p2); //拷贝构造函数

//注意： 调用默认构造函数的时候，不要加（）
// Person p1(); //编译器会认为这是一个函数的声明，不会认为在创建对象
```

### 显示法

```cpp
Person x1;
Person x2 = Person(10); //有参构造
Person x3 = Person(x2); //拷贝构造

//Person(10)这个是匿名对象，特点：当前行执行结束后，系统会立即回收掉匿名对象
//不要利用拷贝构造函数，初始化匿名对象；编译器会认为 Person(p3) 等价于Person p3;
//对象声明会触发重定义；
```

### 隐式转换法

```cpp
Person x4 = 10; //相当于写了 Person p4 =Person(10);
Person x5 = x4; //拷贝构造
```

#### 匿名对象

```cpp
Person(10)这个是匿名对象，特点：当前行执行结束后，系统会立即回收掉匿名对象
```

```cpp
#include<iostream>

using namespace std;

//按照参数分为：有参和无参构造，无参又称为默认构造函数
//按照类型分类分为：普通构造和拷贝构造

class Person {
public:
	//无参（默认）构造函数
	Person() {
		cout << "无参构造函数!" << endl;
	}
	//有参构造函数
	Person(int a) {
		age = a;
		cout << "有参构造函数!" << endl;
	}
	//拷贝构造函数
	Person(const Person& p) {
		age = p.age;//将传入的人身上的所有属性，拷贝到我身上
		cout << "拷贝构造函数!" << endl;
	}

	//析构函数
	~Person() {
		cout << "析构函数!" << endl;
	}
public:
	int age;
};

//2、构造函数的调用
//调用无参构造函数
void test01() {
    //1.括号法
	Person p; //调用无参构造函数
    Person p2(10); //有参构造函数
    Person p3(p2); //拷贝构造函数

    //注意： 调用默认构造函数的时候，不要加（）
    // Person p1(); //编译器会认为这是一个函数的声明，不会认为在创建对象


    cout << "p2年龄:" << p2.age << endl;
    cout << "p3年龄:" << p3.age << endl;

    //2. 显示法
    Person x1;
    Person x2 = Person(10); //有参构造
    Person x3 = Person(x2); //拷贝构造
    //Person(10)这个是匿名对象，特点：当前行执行结束后，系统会立即回收掉匿名对象
    //不要利用拷贝构造函数，初始化匿名对象；编译器会认为 Person(x3) 等价于Person x3;对象声明会触发重定义；

    //3. 隐式转换法
    Person x4 =10; //相当于写了 Person x4 =Person(10);
    Person x5 = x4; //拷贝构造
}

int main(){

    test01();
}
```
