# map/multimap容器

## 1. map基本概念

### **简介：**

* map中所有元素都是pair
* pair中第一个元素为key（键值），起到索引作用，第二个元素为value（实值）
* 所有元素都会根据元素的键值自动排序

### 本质

map / multimap 属于关联式容器，底层结构是用二叉树实现。

**优点：**

* 可以根据key值快速找到value值

map和multimap**区别**：

* map不允许容器中有重复key值元素
* multimap允许容器中有重复key值元素

> value 是可以又重复的

## 2. 构造和赋值

**函数原型：**

**构造：**

* `map<T1, T2> mp;` //map默认构造函数:
* `map(const map &mp);` //拷贝构造函数

**赋值：**

* `map& operator=(const map &mp);` //重载等号操作符

> map中所有元素都是成对出现，插入数据时候要使用对组

[#7.-pair-dui-zu-chuang-jian](setmultiset-rong-qi.md#7.-pair-dui-zu-chuang-jian "mention")

```cpp
#include<iostream>
#include<map>

using namespace std;

void printMap(map<int, int>&m){
    for(map<int,int> :: iterator it = m.begin();it !=m.end(); it++){
        cout << "key= " << (*it).first << "value= " << it->second << endl;
    }
}

void test01(){
    //创建map容器
    map<int , int > m;
    m.insert(pair<int ,int>(1,10));
    m.insert(pair<int ,int>(3,30));
    m.insert(pair<int ,int>(2,20));
    m.insert(pair<int ,int>(4,40));

    printMap(m);

    //拷贝构造
    map<int,int>m2(m);
    printMap(m2);

    //赋值
    map<int,int>m3;
    m3=m2;
    printMap(m3);
}

int main(){
    test01();

}
```

## 3. 大小和交换

* `size();` //返回容器中元素的数目
* `empty();` //判断容器是否为空
* `swap(st);` //交换两个集合容器

```cpp
#include <map>
#include<iostream>

using namespace std;

void printMap(map<int,int>&m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << it->first << " value = " << it->second << endl;
	}
	cout << endl;
}

void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));

	if (m.empty())
	{
		cout << "m为空" << endl;
	}
	else
	{
		cout << "m不为空" << endl;
		cout << "m的大小为： " << m.size() << endl;
	}
}


//交换
void test02()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));

	map<int, int>m2;
	m2.insert(pair<int, int>(4, 100));
	m2.insert(pair<int, int>(5, 200));
	m2.insert(pair<int, int>(6, 300));

	cout << "交换前" << endl;
	printMap(m);
	printMap(m2);

	cout << "交换后" << endl;
	m.swap(m2);
	printMap(m);
	printMap(m2);
}

int main() {

	test01();

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
* `erase(key);` //删除容器中值为key的元素。

#### insert()三种不同插入方法

```cpp
 // 第一种
 m.insert(pair<int,int>(1,10));
 
 //第二种
 m.insert(make_pair(2,20));
 
 //第三种
 m.insert(map<int,int>::value_type(3,30));
 
 //第四种
 m[4] = 40;
```

```cpp
#include<iostream>
#include<map>

using namespace std;

//map 容器 插入和删除

void printMap(map<int,int>&m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << it->first << " value = " << it->second << endl;
	}
	cout << endl;
}

void test01(){

    map<int,int>m;

    //插入
    //第一种
    m.insert(pair<int,int>(1,10));

    //第二种
    m.insert(make_pair(2,20));

    //第三种插入方式
	m.insert(map<int, int>::value_type(3, 30));
	
    //第四种插入方式
	m[4] = 40; 
	printMap(m);

    //删除
    m.erase(m.begin());
    printMap(m);

    m.erase(3); //按照key删除
    printMap(m);

    //清空
	m.erase(m.begin(),m.end());
	m.clear();
	printMap(m);

}

int main(){
    test01();
}
```

## 5. 查找和统计

**函数原型：**

* `find(key);` //查找key是否存在,若存在，**返回该键的元素的迭代器**；若不存在，返回set.end();
* `count(key);` //统计key的元素个数

> map count 而言，要么是 0，要么是 1

```cpp
#include<iostream>
#include<map>

using namespace std;

//map 容器 查找和统计
void test01(){

    //查找
    map<int,int>m;
    m.insert(pair<int,int>(1,10));
    m.insert(pair<int,int>(2,20));
    m.insert(pair<int,int>(3,30));

    map<int,int>::iterator pos = m.find(3);

    if(pos!=m.end()){
        cout << "查到了元素key " <<(*pos).first << "value =" << pos->second << endl;
    }else{
        cout << "未找到元素" << endl;
    }
    //统计
    //map不允许插入重复的 key 元素，count 统计而言，要么是0 要么是 1

    int num = m.count(3);
    cout << num << endl;
}

int main(){
    test01();
}
```

## 6. 容器排序

**主要技术点:**

* 利用仿函数，可以改变排序规则

```cpp
#include<iostream>
#include<string>
#include<map>

using namespace std;
// class Person{
//     public:
//     Person(string name, int age){
//         this->m_Name = name;
//         this-> age = age;
//     }

//     string m_Name;
//     int age;
// };

// class MyCompare { //重载（）
// public:
// 	bool operator()(const Person &p1,const Person &p2) {
// 		return p1.age > p2.age;
// 	}
// };

class MyCompare {
public:
	bool operator()(int v1, int v2) {
		return v1 > v2;
	}
};

// void test02(){
//     map<string,int, MyCompare> m;

//     Person p1("刘备", 23);
// 	Person p2("关羽", 27);
// 	Person p3("张飞", 25);
// 	Person p4("赵云", 21);

//     m.insert(make_pair(p1.m_Name, p1.age));
//     m.insert(make_pair(p2.m_Name, p2.age));
//     m.insert(make_pair(p3.m_Name, p3.age));
//     m.insert(make_pair(p4.m_Name, p4.age));
//     // m.insert(make_pair(p2, MyCompare()));
//     // m.insert(make_pair(p3, MyCompare()));
//     // m.insert(make_pair(p4, MyCompare()));
//     for(map<string,int, MyCompare>::iterator it = m.begin(); it !=m.end() ;it++){
//         cout << "姓名" << it->first << "年龄" << it->first << endl;
//     }
// }

void test01() 
{
	//默认从小到大排序
	//利用仿函数实现从大到小排序
	map<int, int, MyCompare>m; //在这修改排序的顺序，需要用仿函数重载（）
	// map<int,int>m;
	m.insert(make_pair(1, 10));
	m.insert(make_pair(2, 20));
	m.insert(make_pair(3, 30));
	m.insert(make_pair(4, 40));
	m.insert(make_pair(5, 50));

	for (map<int, int, MyCompare>::iterator it = m.begin(); it != m.end(); it++) {
		cout << "key:" << it->first << " value:" << it->second << endl;
	}
	// for (map<int, int>::iterator it = m.begin(); it != m.end(); it++) {
	// 	cout << "key:" << it->first << " value:" << it->second << endl;
	// }
}


int main(){

    test01();
    // test02();
}
```
