# 引用做函数返回值

作用：引用是可以作为函数的返回值存在的

注意：**不要返回局部变量引用**

用法：函数调用作为左值

```cpp
#include<iostream>

using namespace std;

//1. 不要返回局部变量的引用
int& test01(){
    int a =10; //局部变量存放在栈区
    return a;
}

//返回静态变量引用
int& test02() {
	static int a = 20; //静态变量，存在放全局区，在程序结束后才释放
	return a;
}


int main(){

    // 引用做函数的返回值

    //不能返回局部变量的引用
	int& ref = test01();
    cout << "ref = " << ref << endl; //第一次结果正确，是因为编译器做了保留
    cout << "ref = " << ref << endl; //第二次结果为乱码，错误，因为a 的内存已经释放


    //2. 函数的调用可以作为左值
    int& ref2 = test02();

    test02() =1000; //如果函数的返回值是引用，这个函数的调用可以作为左值
    
    cout << "ref2 = " << ref2 << endl;
	cout << "ref2 = " << ref2 << endl;

}
```
