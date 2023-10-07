# 类做友元

friend可以让类作为好朋友，访问类中的私有内容

```cpp
#include<iostream>
#include<string>
using namespace std;

class Building;
class goodGay
{
public:

	goodGay();
	void visit(); //参观函数访问 building 中的属性

private:
	Building *building;
};


class Building
{
	//告诉编译器 goodGay类是Building类的好朋友，可以访问到Building类中私有内容
	friend class goodGay;

public:
	Building();

public:
	string m_SittingRoom; //客厅
private:
	string m_BedRoom;//卧室
};

Building::Building() //类外写成员函数
{
	this->m_SittingRoom = "客厅";
	this->m_BedRoom = "卧室";
}

goodGay::goodGay()
{
	building = new Building; //创建建筑物对象
}

void goodGay::visit()
{
	cout << "好基友正在访问" << building->m_SittingRoom << endl;
	cout << "好基友正在访问" << building->m_BedRoom << endl;
}

void test01()
{
	goodGay gg;
	gg.visit();

}

int main(){

    test01();
}
```
