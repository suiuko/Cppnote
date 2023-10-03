# 引用做函数参数

作用：函数传参时，可以利用引用的技术让形参修饰实参

优点：可以简化指针修改实参

> 值传递，main中不会发生改变。
>
> 地址传递，形参可以修改实参，因为使用了指针
>
> 引用传递，形参可以修改实参

```cpp
#include<iostream>

using namespace std;
//交换函数

//1. 值传递
void mySwap01(int a, int b) {
	int temp = a;
	a = b;
	b = temp;
    cout <<"Swap01内部"<< "a:" << a << " b:" << b << endl;
}

//2. 地址传递
void mySwap02(int* a, int* b) {
	int temp = *a;
	*a = *b;
	*b = temp;
}

//3. 引用传递
void mySwap03(int& a, int& b) {
	int temp = a;
	a = b;
	b = temp;
}


int main(){

    int a =10;
    int b =20;
    mySwap01(a, b); //值传递，没有改变
	cout <<"main中01:"<< "a:" << a << " b:" << b << endl;

    mySwap02(&a, &b); //地址传递，形参会修饰实参
	cout <<"main中02:"<< "a:" << a << " b:" << b << endl;

    mySwap03(a, b); //引用传递，形参会修饰实参
	cout <<"main中03:"<< "a:" << a << " b:" << b << endl;
    //03引用传递是如何运作？ main 中的a传递的时候 我们使用&a，这其实也是取别名的操作，
    //只不过这个别名还是叫a, 这样就能修改实参了
}
```
