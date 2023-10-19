# set/multiset容器

## 1. 基本概念

**本质：**

* set/multiset属于**关联式容器**，底层结构是用**二叉树**实现。

**set和multiset区别**：

* set不允许容器中有重复的元素
* multiset允许容器中有重复的元素

## 2. set构造和赋值

构造：

* `set<T> st;` //默认构造函数：
* `set(const set &st);` //拷贝构造函数

赋值：

* `set& operator=(const set &st);` //重载等号操作符

插入函数：

* insert(num) ; //只有 insert 方式

```cpp
#include<iostream>
#include<set>

using namespace std;

void printSet(set<int> & s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01(){
    set<int> s1;
    s1.insert(10);
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    printSet(s1);

    //拷贝构造
	set<int>s2(s1);
	printSet(s2);

    //赋值
	set<int>s3;
	s3 = s2;
	printSet(s3);
}

int main(){
    test01();
}
```

## 3. set大小和交换

**函数原型：**

* `size();` //返回容器中元素的数目
* `empty();` //判断容器是否为空
* `swap(st);` //交换两个集合容器

```cpp
#include <set>
#include<iostream>

using namespace std;
void printSet(set<int> & s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

//大小
void test01()
{

	set<int> s1;
	
	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);

	if (s1.empty())
	{
		cout << "s1为空" << endl;
	}
	else
	{
		cout << "s1不为空" << endl;
		cout << "s1的大小为： " << s1.size() << endl;
	}

}

//交换
void test02()
{
	set<int> s1;

	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);

	set<int> s2;

	s2.insert(100);
	s2.insert(300);
	s2.insert(200);
	s2.insert(400);

	cout << "交换前" << endl;
	printSet(s1);
	printSet(s2);
	cout << endl;

	cout << "交换后" << endl;
	s1.swap(s2);
	printSet(s1);
	printSet(s2);
}

int main() {

	//test01();

	test02();

	system("pause");

	return 0;
}
```

## 4. 插入和删除

**函数原型：**

* `insert(elem);` //在容器中插入元素。
* `clear();` //清除所有元素
* `erase(pos);` //删除pos迭代器所指的元素，返回下一个元素的迭代器。
* `erase(beg, end);` //删除区间\[beg,end)的所有元素 ，返回下一个元素的迭代器。
* `erase(elem);` //删除容器中值为elem的元素。

```cpp
#include<iostream>
#include <set>

using namespace std;

void printSet(set<int>&s){
    for(set<int>::iterator it = s.begin(); it !=s.end();it++){
        cout << *it << " ";
    }
    cout <<endl;
}

void test01(){
    set<int> s1;
	//插入
	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);
	printSet(s1);

	//删除
	s1.erase(s1.begin()); //已经排序好，默认删除最小的
	printSet(s1);

	s1.erase(30);
	printSet(s1);

	//清空
	//s1.erase(s1.begin(), s1.end());
	s1.clear();
	printSet(s1);
}

int main(){

    test01();
}
```

## 5. 查找和统计

**函数原型：**

* `find(key);` //查找key是否存在,若存在，返回该键的元素的迭代器；若不存在，返回set.end();
* `count(key);` //统计key的元素个数

```cpp
#include<iostream>
#include<set>

using namespace std;

void test01(){
    //查找
    set<int>s1;
    //插入数据
    s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);

    //查找
    set<int>::iterator pos = s1.find(40);
    if (pos != s1.end())
	{
		cout << "找到了元素 ： " << *pos << endl;
	}
	else
	{
		cout << "未找到元素" << endl;
	}
}

//统计
void test02(){
    set<int>s1;
    //插入数据
    s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);

    //统计 30 的个数
    int num = s1.count(30);
    cout << "num = " << num << endl;
}
int main(){
    test01();
    test02();
}
```

## 6. set和multiset区别

**区别：**

* set不可以插入重复数据，而multiset可以
* set插入数据的同时会返回插入结果，表示插入是否成功
* multiset不会检测数据，因此可以插入重复数据

```cpp
#include <set>
#include<iostream>
using namespace std;

//set和multiset区别
void test01()
{
	set<int> s;
	pair<set<int>::iterator, bool>  ret = s.insert(10); // pair 对组
	if (ret.second) { //看 ret 的第二个元素
		cout << "第一次插入成功!" << endl;
	}
	else {
		cout << "第一次插入失败!" << endl;
	}

	ret = s.insert(10);
	if (ret.second) {
		cout << "第二次插入成功!" << endl;
	}
	else {
		cout << "第二次插入失败!" << endl;
	}
    
	//multiset
	multiset<int> ms;
	ms.insert(10);
	ms.insert(10);

	for (multiset<int>::iterator it = ms.begin(); it != ms.end(); it++) {
		cout << *it << " ";
	}
	cout << endl;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 7. pair 对组创建

**功能描述：**

* 成对出现的数据，利用对组可以返回两个数据

**两种创建方式：**

* `pair<type, type> p ( value1, value2 );`
* `pair<type, type> p = make_pair( value1, value2 );`

```cpp
#include <string>

//对组创建
void test01()
{
	pair<string, int> p(string("Tom"), 20);
	cout << "姓名： " <<  p.first << " 年龄： " << p.second << endl;

	pair<string, int> p2 = make_pair("Jerry", 10);
	cout << "姓名： " << p2.first << " 年龄： " << p2.second << endl;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 8. set 容器排序

主要技术点：

* 利用仿函数，可以改变排序规则

### 示例一：set存放内置数据类型

```cpp
#include <set>
#include<iostream>
using namespace std;

class MyCompare 
{
public: 
	bool operator()(int v1, int v2) { //重载小括号
		return v1 > v2;
	}
};
void test01() 
{    
	set<int> s1;
	s1.insert(10);
	s1.insert(40);
	s1.insert(20);
	s1.insert(30);
	s1.insert(50);

	//默认从小到大
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << " ";
	}
	cout << endl;

	//指定排序规则
	set<int,MyCompare> s2;
	s2.insert(10);
	s2.insert(40);
	s2.insert(20);
	s2.insert(30);
	s2.insert(50);

	for (set<int, MyCompare>::iterator it = s2.begin(); it != s2.end(); it++) {
		cout << *it << " ";
	}
	cout << endl;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

### 示例二：set存放自定义数据类型

```cpp
#include<iostream>
#include<set>
#include<string>

using namespace std;

//set 容器排序，存放自定义数据类型

class Person{
    public:
    Person(string name, int age){
        this->m_Name = name;
        this->m_Age = age;
    }

    string m_Name;
    int m_Age;
};


void test01(){
    set<Person>s;

    //创建 Person 对象
    Person p1("刘备", 23);
	Person p2("关羽", 27);
	Person p3("张飞", 25);
	Person p4("赵云", 21);

    s.insert(p1);
	s.insert(p2);
	s.insert(p3);
	s.insert(p4);

    for(set<Person>::iterator it =s.begin(); it !=s.end() ;it++){
        cout << "姓名" << it->m_Name << "年龄" << it->m_Age << endl;
    }

}

int main(){
    test01();
}
```
