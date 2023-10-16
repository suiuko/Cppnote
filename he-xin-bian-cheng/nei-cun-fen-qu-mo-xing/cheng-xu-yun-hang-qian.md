# 程序运行前

在程序编译后，生成了exe可执行程序，**未执行该程序前**分为两个区域

**代码区：**

存放 CPU 执行的机器指令

代码区是**共享**的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可

代码区是**只读**的，使其只读的原因是防止程序意外地修改了它的指令

**全局区：**

全局变量和静态变量存放在此.

全局区还包含了常量区, 字符串常量和其他常量也存放在此.

**该区域的数据在程序结束后由操作系统释放**

> 全局变量和局部变量存放在不同的地方\
> 全局变量和静态变量存在相同的地方

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

//全局变量
int g_a = 10;
int g_b = 10;

int main(){

    //全局区

    //全局变量、静态变量、常量

    //创建普通局部变量


    int a =10;
    int b =10;
    cout << "局部变量a地址为： " << &a << endl;
	cout << "局部变量b地址为： " << &b << endl;

    cout << "全局变量g_a地址为： " <<  &g_a << endl;
	cout << "全局变量g_b地址为： " <<  &g_b << endl;
    //局部变量和全局变量存放的地方不一样
    

    //静态变量
	static int s_a = 10;
	static int s_b = 10;
    cout << "静态变量s_a地址为： " << &s_a << endl;
	cout << "静态变量s_b地址为： " << &s_b << endl;

    //字符串常量
    cout << "字符串常量地址为： " << (int)&"hello world" << endl;
	cout << "字符串常量地址为： " << (int)&"hello world1" << endl;

    // const修饰的变量
    // c-const ; g - global  l-local
    const int c_l_a = 10;
	const int c_l_b = 10;
	cout << "局部常量c_l_a地址为： " << (int)&c_l_a << endl;
	cout << "局部常量c_l_b地址为： " << (int)&c_l_b << endl;
}
```
