# 简单讲解

## 1. vector 存放内置数据类型

容器： `vector`

算法： `for_each`

迭代器： `vector<int>::iterator`

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>
using namespace std;
#include<vector>
#include<algorithm>

//vector 容器存放内置数据类型
void MyPrint(int val){
    cout << val << endl;
}

void test01(){

    //创建了一个 vector 容器，数组
    vector<int> v;
    //向容器放数据
    v.push_back(10);
    v.push_back(20);
    v.push_back(30);
    v.push_back(40);

    //每一个容器都有自己的迭代器，迭代器是用来遍历容器中的元素
	//v.begin()返回迭代器，这个迭代器指向容器中第一个数据
	//v.end()返回迭代器，这个迭代器指向容器元素的最后一个元素的下一个位置
	//vector<int>::iterator 拿到vector<int>这种容器的迭代器类型

	vector<int>::iterator pBegin = v.begin();
	vector<int>::iterator pEnd = v.end();

    //第一种遍历方式
    while(pBegin !=pEnd){
        cout << *pBegin << endl;
        pBegin++;
    }

    //第二种遍历方式
    for(vector<int>::iterator it = v.begin();it!=v.end();it++){
        cout << *it << endl;
    }

    //第三种遍历方式
    //使用 STL 提供的标准遍历算法，头文件 algorithm
    for_each(v.begin(), v.end(), MyPrint);
}

int main(){

    test01();
}
```

## 2.vector 存放自定义数据类型

> \*it是什么就看<>里面是什么，解出来的就是什么&#x20;
>
> 当然it是指针，可以直接使用->来获取数据

```cpp
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;

//vector 容器中存放自定义数据类型

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
    vector<Person>v;
    Person p1("aaa", 10);
    Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);
    v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

    for(vector<Person>::iterator it = v.begin();it!=v.end();it++){
        cout << "name" << (*it).m_Name << " age" << (*it).m_Age << endl; 
        //*it是什么就看<>里面是什么，解出来的就是什么
        //当然it是指针，可以直接使用->来获取数据
        cout << "name" << it->m_Name << " age" << it->m_Age << endl; 

    }
}

void test02(){
    vector<Person*>v;
    Person p1("aaa", 10);
    Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);

    v.push_back(&p1);
	v.push_back(&p2);
	v.push_back(&p3);
	v.push_back(&p4);
	v.push_back(&p5);   
    for(vector<Person*>::iterator it = v.begin();it!=v.end();it++){
        cout << "name" << (*it)->m_Name << " age" << (*it)->m_Age << endl; 
    }
}
int main(){
    test01();
    test02();
}
```

## 3. vector容器嵌套容器

> ```cpp
>     //走大容器，把所有数据走一遍
>     for(vector<vector<int>>::iterator it = v.begin();it !=v.end();it++){
>         //(*it) ---- 容器 vector<int>
>         for(vector<int>::iterator vit=(*it).begin();vit!=(*it).end();vit++){
>             cout << *vit << endl;
>         }
>         cout << endl;
>     }
> ```

```cpp
#include<iostream>
#include<vector>

using namespace std;

void test01(){
    vector<vector<int>> v;
    //创建小容器
    vector<int>v1;
    vector<int>v2;
    vector<int>v3;
    vector<int>v4;
    //向小容器中添加数据
    for(int i =0;i<4;i++){
        v1.push_back(i+1);
        v2.push_back(i+2);
        v3.push_back(i+3);
        v4.push_back(i+4);
    }

    //将小容器插入到大容器v中
        v.push_back(v1);
	v.push_back(v2);
	v.push_back(v3);
	v.push_back(v4);

    //走大容器，把所有数据走一遍
    for(vector<vector<int>>::iterator it = v.begin();it !=v.end();it++){
        //(*it) ---- 容器 vector<int>
        for(vector<int>::iterator vit=(*it).begin();vit!=(*it).end();vit++){
            cout << *vit << endl;
        }
        cout << endl;
    }
}
int main(){

    test01();
}
```
