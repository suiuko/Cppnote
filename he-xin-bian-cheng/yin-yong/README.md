# 引用

作用：给变量起别名

语法：**数据类型 &别名= 原名**

**引用是直接对数据进行修改了，可以在函数中使用引用&别名的方法来代替指针的操作。**

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

int main(){

    int a = 10;
	int &b = a;

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;

	b = 100;

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;

	system("pause");

	return 0;

}
```

## 注意事项

* 引用必须初始化，例如：int \&b; //错误的
* 引用在初始化后，不可以改变
