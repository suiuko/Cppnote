# 详细讲解

## 1. 基本概念

**功能：**

* vector数据结构和**数组非常相似**，也称为**单端数组**

**vector与普通数组区别：**

* 不同之处在于数组是静态空间，而vector可以**动态扩展**

**动态扩展：**

* 并不是在原空间之后续接新空间，而是找更大的内存空间，然后将原数据拷贝新空间，释放原空间

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

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

