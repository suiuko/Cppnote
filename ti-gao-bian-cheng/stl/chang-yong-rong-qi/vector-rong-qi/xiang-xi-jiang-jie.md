# 详细讲解

## 1. 基本概念

**功能：**

* vector数据结构和**数组非常相似**，也称为**单端数组**

**vector与普通数组区别：**

* 不同之处在于数组是静态空间，而vector可以**动态扩展**

**动态扩展：**

* 并不是在原空间之后续接新空间，而是找更大的内存空间，然后将原数据拷贝新空间，释放原空间

<figure><img src="../../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* vector容器的迭代器是支持随机访问的迭代器

## 2. 构造函数

**功能描述：**

* 创建vector容器

**函数原型：**

* `vector<T> v;` //采用模板实现类实现，默认构造函数
* `vector(v.begin(), v.end());` //**将v\[begin(), end())区间**中的元素拷贝给本身。注意：是前闭后开。
* `vector(n, elem);` //构造函数将n个elem拷贝给本身。
* `vector(const vector &vec);` //拷贝构造函数。

```cpp
#include<iostream>
using namespace std;
#include<vector>

void printVector(vector<int>&v){
    for(vector<int>::iterator it = v.begin();it!=v.end();it++){
        cout << *it << " ";
    }
    cout << endl;

}
//vector 构造
void test01(){
    vector<int>v1; //默认构造，无参构造
    
    for(int i=0; i<10;i++){
        v1.push_back(i);
    }
    printVector(v1);

    //通过区间的方式进行构造
    vector<int >v2(v1.begin(),v2.end());
    printVector(v2);

    //N 个 elem 来构造
    vector<int> v3(10,100);
    printVector(v3);

    //拷贝构造
    vector<int> v4(v3);
	printVector(v4);
}

int main(){

    test01();
}
```

## 3. 赋值操作

**功能描述：**

* 给vector容器进行赋值

**函数原型：**

* `vector& operator=(const vector &vec);`//重载等号操作符
* `assign(beg, end);` //将\[beg, end)区间中的数据拷贝赋值给本身。
* `assign(n, elem);` //将n个elem拷贝赋值给本身。

```cpp
#include<iostream>
#include<vector>

using namespace std;

//打印
void printVector(vector<int>&v){
    for(vector<int>::iterator it = v.begin();it!=v.end();it++){
        cout << *it << " ";
    }
    cout << endl;
}

//vector赋值
void test01(){
    vector<int> v1;
    for(int i=0;i<10;i++){
        v1.push_back(i);
    }
    printVector(v1);

    //赋值 operator = 
    vector<int> v2;
    v2 = v1;
    printVector(v2);

    //assign 拷贝
    vector<int>v3;
    v3.assign(v1.begin(),v1.end());
    printVector(v3);

    //N 个 elem 方式赋值
    vector<int>v4;
    v4.assign(10,100);
    printVector(v4);

}

int main(){
    test01();

}
```

## 4. 容量和大小

**功能描述：**

* 对vector容器的容量和大小操作

**函数原型：**

* `empty();` //判断容器是否为空
* `capacity();` //容器的容量
* `size();` //返回容器中元素的个数
*   `resize(int num);` //重新指定容器的长度为num，若容器变长，则以默认值填充新位置。

    //如果容器变短，则末尾超出容器长度的元素被删除。
*   `resize(int num, elem);` //重新指定容器的长度为num，若容器变长，则以elem值填充新位置。

    //如果容器变短，则末尾超出容器长度的元素被删除

```cpp
#include<iostream>
#include<vector>

using namespace std;

void printVector(vector<int> &v){
    for(vector<int>::iterator it = v.begin();it!=v.end();it++){
        cout << *it <<" ";
    }
    cout << endl;
}

void test01(){
    vector<int>v1;
    for(int i=0;i<10;i++){
        v1.push_back(i);
    }
    printVector(v1);
    if(v1.empty()){
        cout << "v1为空" << endl;
    }else{
        cout << "v1不为空" << endl;
        cout << "容量 = " << v1.capacity() << endl;
        cout << "大小 = " << v1.size() << endl;
    }

    //resize 重新指定大小，若指定的更大，默认用 0 填充新位置，可以利用重载版本替换默认填充
    v1.resize(15,10);
    printVector(v1);

    //resize 重新指定大小， 若指定的更小，超出部分元素被删除
    v1.resize(5);
}

int main(){
    test01();

}
```

## 5. 插入和删除

**功能描述：**

* 对vector容器进行插入、删除操作

**函数原型：**

* `push_back(ele);` //尾部插入元素ele
* `pop_back();` //删除最后一个元素
* `insert(const_iterator pos, ele);` //迭代器指向位置pos插入元素ele
* `insert(const_iterator pos, int count,ele);`//迭代器指向位置pos插入count个元素ele
* `erase(const_iterator pos);` //删除迭代器指向的元素
* `erase(const_iterator start, const_iterator end);`//删除迭代器从start到end之间的元素
* `clear();` //删除容器中所有元素

总结：

* 尾插 --- push\_back
* 尾删 --- pop\_back
* 插入 --- insert (位置迭代器)
* 删除 --- erase （位置迭代器）
* 清空 --- clear

```cpp
#include<iostream>
#include<vector>

using namespace std;

void printVector(vector<int>&v){
    for(vector<int>::iterator it =v.begin();it!=v.end();it++){
        cout << *it << " ";
    }
    cout << endl;
}

//插入和删除
void test01(){
    vector<int> v1;

    v1.push_back(10);
    v1.push_back(10);
    v1.push_back(10);
    v1.push_back(10);
    printVector(v1);

    //尾删
    v1.pop_back();
    printVector(v1);

    //插入
    v1.insert(v1.begin(),100);
    printVector(v1);

    v1.insert(v1.begin(), 2, 1000);
    printVector(v1);

    //删除
    v1.erase(v1.begin());
    printVector(v1);

    //清空
    v1.erase(v1.begin(),v1.end());
    v1.clear();
    printVector(v1);
}

int main(){
    test01();
}
```

## 6. 数据存取

**功能描述：**

* 对vector中的数据的存取操作

**函数原型：**

* `at(int idx);` //返回索引idx所指的数据
* `operator[];` //返回索引idx所指的数据
* `front();` //返回容器中第一个数据元素
* `back();` //返回容器中最后一个数据元素

```cpp
#include <vector>

void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}

	for (int i = 0; i < v1.size(); i++)
	{
		cout << v1[i] << " ";
	}
	cout << endl;

	for (int i = 0; i < v1.size(); i++)
	{
		cout << v1.at(i) << " ";
	}
	cout << endl;

	cout << "v1的第一个元素为： " << v1.front() << endl;
	cout << "v1的最后一个元素为： " << v1.back() << endl;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 7. 互换容器

**功能描述：**

* 实现两个容器内元素进行互换

**函数原型：**

* `swap(vec);` // 将vec与本身的元素互换

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

```cpp
#include <vector>

void printVector(vector<int>& v) {

	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << " ";
	}
	cout << endl;
}

//1. 基本使用
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);

	vector<int>v2;
	for (int i = 10; i > 0; i--)
	{
		v2.push_back(i);
	}
	printVector(v2);

	//互换容器
	cout << "互换后" << endl;
	v1.swap(v2);
	printVector(v1);
	printVector(v2);
}

//实际用途， 巧用swap 开业收缩内存空间
void test02()
{
	vector<int> v;
	for (int i = 0; i < 100000; i++) {
		v.push_back(i);
	}

	cout << "v的容量为：" << v.capacity() << endl;
	cout << "v的大小为：" << v.size() << endl;

	v.resize(3);

	cout << "v的容量为：" << v.capacity() << endl;
	cout << "v的大小为：" << v.size() << endl;

	//收缩内存
	vector<int>(v).swap(v); //匿名对象

	cout << "v的容量为：" << v.capacity() << endl;
	cout << "v的大小为：" << v.size() << endl;
}

int main() {

	test01();

	test02();

	system("pause");

	return 0;
}
```

## 8. 预留空间

**功能描述：**

* 减少vector在动态扩展容量时的扩展次数

**函数原型：**

* `reserve(int len);`//容器预留len个元素长度，预留位置不初始化，元素不可访问。

```cpp
#include <vector>

void test01()
{
	vector<int> v;

	//预留空间
	v.reserve(100000);

	int num = 0; //统计开辟的次数
	int* p = NULL;
	for (int i = 0; i < 100000; i++) {
		v.push_back(i);
		if (p != &v[0]) { //开辟内存次数的过程
			p = &v[0];
			num++;
		}
	}

	cout << "num:" << num << endl;
}

int main() {

	test01();
    
	system("pause");

	return 0;
}
```
