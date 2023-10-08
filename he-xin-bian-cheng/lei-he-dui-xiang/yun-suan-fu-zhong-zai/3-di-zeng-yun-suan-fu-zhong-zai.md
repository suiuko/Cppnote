# 3 递增运算符重载

> 前置是增完取值，后置是先取值后增

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

> 在重载前置运算符中，为什么返回的是引用而不是数值？\
> 因为是数值的话，返回的是新变量，在新变量进行++操作，而不是之前操作的变量，可以通过输出两次来查看。
>
> void operator++(int),这个int代表占位参数，可以用于区分前置和后置。
>
> 在后置运算符中，需要返回数值，不能返回引用；\
> 因为在MyInteger temp = \*this; 这时候变量会被释放，如果再使用引用会有非法操作。

```cpp
#include<iostream>

using namespace std;

class MyInteger{
    friend ostream& operator<<(ostream& out, MyInteger myint);
    public:
    MyInteger() {
		m_Num = 0;
	}

    //重载前置++运算符
    MyInteger& operator++() { //为什么要返回的是引用不是数值？
                                //因为返回是新变量，还不是要操作的那个
                                //可以设置两个输出看一下，只有第一个成功，第二个失败。
		//先++运算
		m_Num++;
		//再将自身返回
		return *this;
	}

    //重载后置++运算符
    MyInteger operator++(int){ //这个int代表占位参数，可以用于区分前置和后置。
                                //这里是需要返回值，而不是引用
        //先返回
		MyInteger temp = *this; //记录当前本身的值，然后让本身的值加1，但是返回的是以前的值，达到先返回后++；
		m_Num++;
		return temp; //最后将记录结果做返回
    }

    private:
	int m_Num;
};

//左重载实现函数
ostream& operator<<(ostream& out, MyInteger myint) {
	out << myint.m_Num;
	return out;
}


void test01() {
	MyInteger myInt;
	cout << ++myInt << endl;
	cout << myInt << endl;
}
void test02(){
    MyInteger myInt;
    cout << myInt++ << endl;
    cout << myInt << endl;
}

int main(){
    // test01();
    test02();
}
```
