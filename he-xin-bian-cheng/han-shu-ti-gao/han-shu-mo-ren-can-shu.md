# 函数默认参数

函数的星灿列表中的形参是可以有默认值的

语法： 返回值类型 函数名 (参数 = 默认值)

> 如果某个位置已经有了默认参数，那么从这个位置往后，从左到右都必须要有默认值。
>
> 如果函数声明有默认参数，函数实现就不能有默认参数

```cpp
#include<iostream>

using namespace std;

int func(int a, int b = 10, int c = 10) {
	return a + b + c;
}

//1. 如果某个位置参数有默认值，那么从这个位置往后，从左向右，必须都要有默认值
//2. 如果函数声明有默认值，函数实现的时候就不能有默认参数
int func2(int a = 10, int b = 10);
int func2(int a, int b) {
	return a + b;
}

int main(){
    cout << "ret = " << func(20, 20) << endl;
	cout << "ret = " << func(100) << endl;

}
```
