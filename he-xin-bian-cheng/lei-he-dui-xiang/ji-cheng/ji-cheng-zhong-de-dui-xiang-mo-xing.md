# 继承中的对象模型

&#x20;问题： 从父类继承过来的成员，哪些属于子类对象中？

> 利用开发人员命令提示工具查看对象模型
>
> cl /d1 reportSingleClassLayout类名 文件名

```cpp
#include<iostream>

using namespace std;


class Base
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C; //私有成员只是被隐藏了，但是还是会继承下去
};

//公共继承
class Son :public Base
{
public:
	int m_D;
};

void test01()
{   
    //父类中的所有非静态成员属性都会被子类继承下去
	cout << "sizeof Son = " << sizeof(Son) << endl;
}

int main(){
    test01();

}
```
