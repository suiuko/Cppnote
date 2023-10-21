# 谓词

## 概念

**概念：**

* 返回bool类型的仿函数称为**谓词**
* 如果operator()接受一个参数，那么叫做一元谓词
* 如果operator()接受两个参数，那么叫做二元谓词

## 1. 一元谓词

只接受一个参数

```cpp
#include<vector>
#include<algorithm>
#include<iostream>

using namespace std;

//1.一元谓词
struct GreaterFive{
	bool operator()(int val) {
		return val > 5;
	}
};

void test01() {

	vector<int> v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}

	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive()); //匿名的函数对象
  //正常情况需要创建根据类来创建一个对象，刚进去，但是如果不想给对象起名，可以还用匿名对象
	if (it == v.end()) {
		cout << "没找到!" << endl;
	}
	else {
		cout << "找到:" << *it << endl;
	}

}

int main(){
    test01();
}
```

## 2. 二元谓词

```cpp
#include<iostream>
#include<vector>
using namespace std;

//二元谓词
class MyCompare
{
public:
	bool operator()(int num1, int num2)
	{
		return num1 > num2;
	}
};

void test01()
{
	vector<int> v;
	v.push_back(10);
	v.push_back(40);
	v.push_back(20);
	v.push_back(30);
	v.push_back(50);

	//默认从小到大
	// sort(v.begin(), v.end());
	// for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	// {
	// 	cout << *it << " ";
	// }
	// cout << endl;

    //使用函数对象改变算法策略，排序从大到小
	sort(v.begin(), v.end(), MyCompare());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}



int main(){

    test01();
}
```
