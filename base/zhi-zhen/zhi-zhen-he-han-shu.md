# 指针和函数

利用指针作函数参数，可以修改实参的值

### 展示：值传递、地址传递



<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

void swap01(int a, int b){

    int temp = a;
    a = b;
    b = temp;
}

void swap02(int *p1,int *p2){
    int temp = *p1;
    *p1 = *p2;
    *p2 = temp;
}

int main(){

    //指针和函数
    //1. 值传递
    int a =10;
    int b= 20;
    swap01(a,b);
    
    cout << "a=" <<a<<endl;
    cout << "b=" <<b<<endl;

    //2. 地址传递
    swap02(&a,&b);
    cout << "地址传递后" << endl;
    cout << "a=" <<a<<endl;
    cout << "b=" <<b<<endl;
}
```
