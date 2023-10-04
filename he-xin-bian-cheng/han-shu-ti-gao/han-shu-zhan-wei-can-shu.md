# 函数占位参数

&#x20;函数中的形参列表里可以有占位参数，用来做占位，调用函数时必须填补该位置。

**语法：** `返回值类型 函数名 (数据类型){}`

```cpp
#include<iostream>

using namespace std;
void func(int a, int) { //目前，占位参数用不到，后面会用到。占位参数也可以有默认参数
	cout << "this is func" << endl;
}
int main(){
    func(10,10); //占位参数必须填补

}
```
