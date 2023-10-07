# 2 左移运算符重载

作用：可以输出自定义数据类型

```cpp
#include<iostream>

using namespace std;

class Person{

    //因为我们改为private，所以元素访问不到，需要用友元来访问
    friend ostream & operator<<(ostream &cout , Person &p);

    public:
    //利用成员函数重载 左移运算符 p.operator<<(cout) 简化版本 p << cout
    //不会利用成员函数重载<<运算符，因为无法实现cout在左侧
	//void operator<<(Person& p){
	//}

    // int m_A;
    // int m_B; //通常情况 需要私有化GOTO private
    Person(int a,int b){
        m_A = a;
        m_B = b;
    }
    private:
    int m_A;
    int m_B;

};

//只能利用全局函数重载左移运算符
// void operator<<(ostream &cout , Person &p){//本质 operator<<(cout ,p)  简化: cout <<p
//     cout << "m_A=" << p.m_A << "m_B=" << p.m_B;
// } 

ostream & operator<<(ostream &cout , Person &p){//本质 operator<<(cout ,p)  简化: cout <<p
    cout << "m_A=" << p.m_A << "m_B=" << p.m_B;
    return cout;
} //ostream &的原因是需要在cout << p后加 << endl;



void test01(){
    Person p(10,10);
    // p.m_A = 10;
    // p.m_B = 10;

    // cout << p.m_A << endl;
    cout << p << endl;
}

int main(){

    test01();
}
```
