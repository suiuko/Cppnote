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

