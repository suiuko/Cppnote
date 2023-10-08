# 深拷贝与浅拷贝

浅拷贝：简单的赋值拷贝操作

深拷贝：在堆区重新申请空间，进行拷贝操作

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

{% content-ref url="../yun-suan-fu-zhong-zai/4-fu-zhi-yun-suan-fu-zhong-zai.md" %}
[4-fu-zhi-yun-suan-fu-zhong-zai.md](../yun-suan-fu-zhong-zai/4-fu-zhi-yun-suan-fu-zhong-zai.md)
{% endcontent-ref %}

```cpp
#include<iostream>

using namespace std;

class Person {
public:
	//无参（默认）构造函数
	Person() {
		cout << "无参构造函数!" << endl;
	}
	//有参构造函数
	Person(int age ,int height) {
		
		cout << "有参构造函数!" << endl;

		m_age = age;
		m_height = new int(height);
		
	}
    //自己实现一个拷贝构造函数，来解决浅拷贝带来的问题
	//拷贝构造函数  
	Person(const Person& p) {
		cout << "拷贝构造函数!" << endl;
		//如果不利用深拷贝在堆区创建新内存，会导致浅拷贝带来的重复释放堆区问题
		m_age = p.m_age;
        //m_height = p.m_height 编译器默认实现就是这行代码
		m_height = new int(*p.m_height); //深拷贝操作
		
	}

	//析构函数
	~Person() {
		cout << "析构函数!" << endl;
		if (m_height != NULL)
		{
			delete m_height; //因为是手动开辟，所以需要手动删除
		}
	}
public:
	int m_age;
	int* m_height;
};

void test01()
{
	Person p1(18, 180);

	Person p2(p1);

	cout << "p1的年龄： " << p1.m_age << " 身高： " << *p1.m_height << endl;

	cout << "p2的年龄： " << p2.m_age << " 身高： " << *p2.m_height << endl;
}

int main(){


}
```
