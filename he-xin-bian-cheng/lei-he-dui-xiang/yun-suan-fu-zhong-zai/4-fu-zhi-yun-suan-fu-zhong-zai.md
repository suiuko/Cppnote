# 4 赋值运算符重载

c++编译器至少给一个类添加4个函数

1. 默认构造函数(无参，函数体为空)
2. 默认析构函数(无参，函数体为空)
3. 默认拷贝构造函数，对属性进行值拷贝
4. **赋值运算符 operator=, 对属性进行值拷贝**

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% content-ref url="../dui-xiang-de-chu-shi-hua-he-qing-li/shen-kao-bei-yu-qian-kao-bei.md" %}
[shen-kao-bei-yu-qian-kao-bei.md](../dui-xiang-de-chu-shi-hua-he-qing-li/shen-kao-bei-yu-qian-kao-bei.md)
{% endcontent-ref %}

```cpp
#include<iostream>

using namespace std;

//赋值运算符 重载

class Person{
    public:
    Person(int age){
      m_Age = new int(age); //堆区
    }

    //重载赋值运算符 
	Person& operator=(Person &p)
	{
        //编译器提供的代码是浅拷贝
		//m_Age = p.m_Age;

         //先应该判断是狗有属性在堆区，如果有先释放干净，然后再深拷贝
		if (m_Age != NULL)
		{
			delete m_Age;
			m_Age = NULL;
		}
	
		//提供深拷贝 解决浅拷贝的问题
		m_Age = new int(*p.m_Age);

		//返回自身
		return *this;
	}

    ~Person(){
        if(m_Age!=NULL){
            delete m_Age;
            m_Age =NULL;
        }
    }

    int *m_Age; //因为手动创建堆区，所以需要用指针
};

void test01(){
    Person p1(18);
    Person p2(20);
	Person p3(30);

	p3 = p2 = p1; //赋值操作

	cout << "p1的年龄为：" << *p1.m_Age << endl;

	cout << "p2的年龄为：" << *p2.m_Age << endl;

	cout << "p3的年龄为：" << *p3.m_Age << endl;
}

int main(){
    test01();

}
```
