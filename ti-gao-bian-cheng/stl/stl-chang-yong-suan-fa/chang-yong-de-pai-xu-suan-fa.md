# 常用的排序算法

**算法简介：**

* `sort` //对容器内元素进行排序
* `random_shuffle` //洗牌 指定范围内的元素随机调整次序
* `merge` // 容器元素合并，并存储到另一容器中
* `reverse` // 反转指定范围的元素

## 1. sort

**功能描述：**

* 对容器内元素进行排序

**函数原型：**

*   `sort(iterator beg, iterator end, _Pred);`

    // 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置

    // beg 开始迭代器

    // end 结束迭代器

    // \_Pred 谓词

```cpp
#include <algorithm>
#include <vector>
#include<iostream>
using namespace std;

void myPrint(int val)
{
	cout << val << " ";
}

void test01() {
	vector<int> v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(20);
	v.push_back(40);

	//sort默认从小到大排序
	sort(v.begin(), v.end());
	for_each(v.begin(), v.end(), myPrint);
	cout << endl;

    //第二种方法
    for(vector<int>::iterator it = v.begin();it!=v.end();it++){
        cout << *it << " ";
    }
    cout << endl;

	//从大到小排序
	sort(v.begin(), v.end(), greater<int>()); //看一下关系反函数
	for_each(v.begin(), v.end(), myPrint);
	cout << endl;

    
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 2. random\_shuffle

**功能描述：**

* 洗牌 指定范围内的元素随机调整次序

**函数原型：**

*   `random_shuffle(iterator beg, iterator end);`

    // 指定范围内的元素随机调整次序

    // beg 开始迭代器

    // end 结束迭代器

```cpp
#include <algorithm>
#include <vector>
#include <ctime>
#include<iostream>

using namespace std;

class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	srand((unsigned int)time(NULL)); //加上随机数种子 随机更好
	vector<int> v;
	for(int i = 0 ; i < 10;i++)
	{
		v.push_back(i);
	}
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;

	//打乱顺序
	random_shuffle(v.begin(), v.end());
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;
}

int main() {

	test01();

	system("pause");

	return 0;
}
```

## 3. merge

**功能描述：**

* 两个容器元素合并，并存储到另一容器中

**函数原型：**

*   `merge(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);`

    // 容器元素合并，并存储到另一容器中

    // 注意: **两个容器必须是有序的**

    // beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

