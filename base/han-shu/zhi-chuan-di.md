# 值传递

在进行函数调用中，主函数中的实参是不会因为另外的函数交换而改变

```cpp
#include<iostream>

using namespace std;


void swap(int num1, int num2){
    cout << "交换前" << endl;
    cout << "num1 ="  << num1 << endl;
    cout << "num2 ="  << num2 << endl;
    
    int temp = num1;
    num1 = num2;
    num2 = temp;
    
    cout << "交换后" << endl;
    cout << "num1 ="  << num1 << endl;
    cout << "num2 ="  << num2 << endl;

}

int main(){
    int a =10;
    int b =20;
    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    
    //当我们做值传递的时候，函数的形参发生改变，并不会影响实参
    swap(a,b);
    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
}
```
