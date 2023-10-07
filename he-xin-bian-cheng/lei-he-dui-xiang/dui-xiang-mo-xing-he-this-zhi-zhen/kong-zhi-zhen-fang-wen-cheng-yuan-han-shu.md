# 空指针访问成员函数

C++中空指针也是可以调用成员函数的，但是也要注意有没有用到this指针

如果用到this指针，需要加以判断保证代码的健壮性

```cpp
#include<iostream>

using namespace std;

class Person{
    public:
    void showClassName(){
        cout << "this is Person class" << endl;
    }

    void showPersonAge(){
        
        if(this == NULL){
            return;
        }
        cout << "age = " << this->m_Age <<endl;

    }
    int m_Age;
};

void test01(){
    Person *p = NULL;
    p->showClassName(); //没有错误

    p->showPersonAge(); //因为指针指向空，但是在调用的时候 用了 this 来获取数据，肯定是错误的。

}
int main(){

    test01();
}
```
