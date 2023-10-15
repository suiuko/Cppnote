# 程序运行后

## **栈区：**

由编译器自动分配释放, 存放函数的形参，局部变量等

注意事项：不要返回局部变量的地址，栈区开辟的数据由编译器自动释放

```cpp
#include<iostream>

using namespace std;

//栈区数据注意事项 -- 不要返回局部变量的地址
//栈区的数据由编译器管理开辟和释放

int * func()
{
	int a = 10; //局部变量，存放在栈区，栈区的数据在函数执行完后自动释放
	return &a; //返回局部变量的地址
}
int main(){

    //接受func函数的返回值
    int *p = func();

    cout << *p << endl; //第一次打印正确的数字，是因为编译器做了保留
	cout << *p << endl; //第二次就不保留了
    
    system("pause");
}
```

## **堆区：**

由程序员分配释放,若程序员不释放,程序结束时由操作系统回收

在C++中主要利用new在堆区开辟内存

> 指针本身也是局部变量，放在栈上，指针保存的数据存在堆区

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



## new操作符

C++中利用new操作符在堆区开辟数据

堆区开辟的数据，由程序员手动开辟，手动释放，释放利用操作符delete

语法：new 数据类型

利用new创建的数据，会返回该数据对应的类型的指针

> 如果想创建一个数字的话，就是用int \*a = new int(数字);  删除使用delete a;
>
> 创建一个数组的话 int \*arr = new int\[元素个数]; 删除使用delete \[] arr;

```cpp
#include<iostream>

using namespace std;
//1.new 的基本语法
int* func()
{
	int* a = new int(10);
	return a;
}

void test01(){

    int *p = func();
    cout << *p << endl;
    //堆区的数据由程序员管理开辟，程序员管理释放
    //如果释放，使用 delete
    delete p;
}


//2.在堆区利用new开辟数组
void test02(){
    //创建 10 整型数据的数组，在堆区
    int * arr = new int [10]; //10代表数组中有 10 个元素
    for(int i =0;i<10;i++){
        arr[i] = i+100;
    }
    for(int i=0;i<10;i++){
        cout << arr[i] << endl;
    }

    //释放堆区数组
    //释放数组的时候  需要加[]才可以
    delete[] arr;

}

int main(){

    test01(); //一个数字
    test02(); // 开辟数组

}
```
