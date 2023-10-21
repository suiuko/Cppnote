# 常用查找算法

**算法简介：**

* `find` //查找元素
* `find_if` //按条件查找元素
* `adjacent_find` //查找相邻重复元素
* `binary_search` //二分查找法
* `count` //统计元素个数
* `count_if` //按条件统计元素个数

## 1. find

**功能描述：**

* 查找指定元素，找到返回指定元素的迭代器，找不到返回结束迭代器end( )

**功能描述：**

* 查找指定元素，**找到返回指定元素的迭代器**，找不到返回结束迭代器end( )

**函数原型：**

*   `find(iterator beg, iterator end, value);`

    // 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

    // beg 开始迭代器

    // end 结束迭代器

    // value 查找的元素

```cpp
#include <algorithm>
#include <vector>
#include <string>
#include<iostream>

using namespace std;

void test01() {

	vector<int> v;
	for (int i = 0; i < 10; i++) {
		v.push_back(i + 1);
	}
	//查找容器中是否有 5 这个元素
	vector<int>::iterator it = find(v.begin(), v.end(), 5);
	if (it == v.end()) 
	{
		cout << "没有找到!" << endl;
	}
	else 
	{
		cout << "找到:" << *it << endl;
	}
}

class Person {
public:
	Person(string name, int age) 
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	//重载== 底层的 find 知道如何对比 person 数据类型
	bool operator==(const Person& p) 
	{
		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age) 
		{
			return true;
		}
		return false;
	}

public:
	string m_Name;
	int m_Age;
};

void test02() {

	vector<Person> v;

	//创建数据
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);

	vector<Person>::iterator it = find(v.begin(), v.end(), p2);
	if (it == v.end()) 
	{
		cout << "没有找到!" << endl;
	}
	else 
	{
		cout << "找到姓名:" << it->m_Name << " 年龄: " << it->m_Age << endl;
	}
}
```

## 2. find\_if

**功能描述：**

* 查找相邻重复元素

**函数原型：**

*   `find_if(iterator beg, iterator end, _Pred);`

    // 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

    // beg 开始迭代器

    // end 结束迭代器

    // \_Pred 函数或者谓词（返回bool类型的仿函数）

```cpp
#include<iostream>
#include<vector>
#include<string>
#include<algorithm>

using namespace std;

//内置数据类型
class GreaterFive
{
public:
	bool operator()(int val)
	{
		return val > 5;
	}
};

void test01() {

	vector<int> v;
	for (int i = 0; i < 10; i++) {
		v.push_back(i + 1);
	}

	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());
	if (it == v.end()) {
		cout << "没有找到!" << endl;
	}
	else {
		cout << "找到大于5的数字:" << *it << endl;
	}
}

//自定义数据类型
class Person {
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
public:
	string m_Name;
	int m_Age;
};

class Greater20
{
public:
	bool operator()(Person &p)
	{
		return p.m_Age > 20;
	}

};

void test02() {

	vector<Person> v;

	//创建数据
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);

	vector<Person>::iterator it = find_if(v.begin(), v.end(), Greater20());
	if (it == v.end())
	{
		cout << "没有找到!" << endl;
	}
	else
	{
		cout << "找到姓名:" << it->m_Name << " 年龄: " << it->m_Age << endl;
	}
}

int main() {

	//test01();

	test02();

	system("pause");

	return 0;
}
```

## 3. adjacent\_find

**功能描述：**

* 查找相邻重复元素

**函数原型：**

*   `adjacent_find(iterator beg, iterator end);`

    // **查找相邻重复元素**,返回相邻元素的第一个位置的迭代器

    // beg 开始迭代器

    // end 结束迭代器

```cpp
#include <algorithm>
#include <vector>
#include<iostream>

using namespace std;


void test01()
{
	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(5);
	v.push_back(2);
	v.push_back(4);
	v.push_back(4);
	v.push_back(3);

	//查找相邻重复元素
	vector<int>::iterator it = adjacent_find(v.begin(), v.end());
	if (it == v.end()) {
		cout << "找不到!" << endl;
	}
	else {
		cout << "找到相邻重复元素为:" << *it << endl;
	}
}

int main(){
    test01();
}
```

## 4. binary\_search

**功能描述：**

* 查找指定元素是否存在(有序)

**函数原型：**

*   `bool binary_search(iterator beg, iterator end, value);`

    // 查找指定的元素，查到 返回true 否则false

    // 注意: 在**无序序列中不可用**

    // beg 开始迭代器

    // end 结束迭代器

    // value 查找的元素

```cpp
#include <algorithm>
#include <vector>
#include<iostream>

using namespace std;

void test01()
{
	vector<int>v;

	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	//二分查找
	bool ret = binary_search(v.begin(), v.end(),2);
	if (ret)
	{
		cout << "找到了" << endl;
	}
	else
	{
		cout << "未找到" << endl;
	}
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 5. count

**功能描述：**

* 统计元素个数

**函数原型：**

*   `count(iterator beg, iterator end, value);`

    // 统计元素出现次数

    // beg 开始迭代器

    // end 结束迭代器

    // value 统计的元素

```cpp
#include <algorithm>
#include <vector>
#include<iostream>

using namespace std;

//内置数据类型
void test01()
{
	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(4);
	v.push_back(5);
	v.push_back(3);
	v.push_back(4);
	v.push_back(4);

	int num = count(v.begin(), v.end(), 4);

	cout << "4的个数为： " << num << endl;
}

//自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	bool operator==(const Person & p)
	{
		if (this->m_Age == p.m_Age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	string m_Name;
	int m_Age;
};

void test02()
{
	vector<Person> v;

	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 30);
	Person p5("曹操", 25);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);
    
    Person p("诸葛亮",35);

	int num = count(v.begin(), v.end(), p);
	cout << "num = " << num << endl;
}
int main() {

	//test01();

	test02();

	system("pause");

	return 0;
}
```

## 6. **count\_if**

**功能描述：**

* 按条件统计元素个数

**函数原型：**

*   `count_if(iterator beg, iterator end, _Pred);`

    // 按条件统计元素出现次数

    // beg 开始迭代器

    // end 结束迭代器

    // \_Pred 谓词

```cpp
#include <algorithm>
#include <vector>

#include<iostream>
using namespace std;

class Greater4
{
public:
	bool operator()(int val)
	{
		return val >= 4;
	}
};

//内置数据类型
void test01()
{
	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(4);
	v.push_back(5);
	v.push_back(3);
	v.push_back(4);
	v.push_back(4);

	int num = count_if(v.begin(), v.end(), Greater4());

	cout << "大于4的个数为： " << num << endl;
}

//自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}

	string m_Name;
	int m_Age;
};

class AgeLess35
{
public:
	bool operator()(const Person &p)
	{
		return p.m_Age < 35;
	}
};
void test02()
{
	vector<Person> v;

	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 30);
	Person p5("曹操", 25);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

	int num = count_if(v.begin(), v.end(), AgeLess35());
	cout << "小于35岁的个数：" << num << endl;
}


int main() {

	//test01();

	test02();

	system("pause");

	return 0;
}
```
