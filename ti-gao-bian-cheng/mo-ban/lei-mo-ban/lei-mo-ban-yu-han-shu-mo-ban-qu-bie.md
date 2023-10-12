# 类模板与函数模板区别

类模板与函数模板区别主要有两点：

1. 类模板没有自动类型推导的使用方式
2. 类模板在模板参数列表中可以有默认参数

```cpp
#include<iostream>

using namespace std;

template<class NameType,class AgeType = int>
class Person{
    public:
    Person(NameType name, AgeType age){
        this->mName = name;
        this->mAge = age;
    }

    void showPerson(){
        cout<< this->mName << " " << this->mAge << endl;
    }

    NameType mName;
    AgeType mAge;
};

//1.类模板没有自动类型推导使用方式
void test01(){
    // Person p ("孙悟空",100); // 错误，类模板使用的时候，不可能用自动类型推导；
    Person<string,int>p("孙悟空",100); //必须使用显示指定类型的方式，使用类模板
    p.showPerson();
}
//2、类模板在模板参数列表中可以有默认参数
void test02()
{
	Person <string> p("猪八戒", 999); //类模板中的模板参数列表 可以指定默认参数
	p.showPerson();
}

int main(){

    test01();

	test02();
}
```
