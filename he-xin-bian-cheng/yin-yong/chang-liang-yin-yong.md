# 常量引用

**作用：**常量引用主要用来修饰形参，防止误操作

在函数形参列表中，可以加const修饰形参，防止形参改变实参。

如果是：

```cpp
void showValue(int& v) {
	v=1000;
	cout << v << endl;
}
int main(){

	int a = 10;
	showValue(a);
	}
//本来要打印 a =10；但是在函数中一不小心修改为 1000，这样是不对的，这样会让a变成 1000 了。
```

所以 需要在函数的参数引用中加const，这样在函数的内部就不会出现误操作了。

```cpp
#include<iostream>

using namespace std;

// void showValue(int& v) {
// 	v=1000; //不小心修改了，这时，a 也变为 1000 了。
// 	cout << v << endl;
// }

//引用使用的场景，通常用来修饰形参
void showValue(const int& v) {
	//v += 10; //报错，不能修改！
	cout << v << endl;
}

int main(){

    //常量引用
    //使用场景： 用来修饰形参，防止误操作。

    //加上const之后，编译器将代码修改， int temp = 10; const int &ref = temp;
    const int &ref = 10; //引用必须引一块合法的内存空间，这里其实引用的是一个临时的空间。
    // ref = 20;  //错误，不能修改

    //函数中利用常量引用防止误操作修改实参
	int a = 10;
	showValue(a);

    cout << "main a:" << a << endl;
}
```
