# 结构体数组

作用：将自定义的结构体放入到数组中方便维护

语法：struct 结构体名 数组名\[元素个数] = \{{ } , { },.. { } }

```cpp
#include<iostream>

using namespace std;

struct student{

    //姓名
    string name;
    //年龄
    int age;
    //分数
    int score;
};

int main(){
    //2. 创建结构体数组
    struct student stuArray[3]={
        {"张三",18,100},
        {"lisi",28,99},
        {"wuwang",38,66}
    };

    //3.给结构体数组中的元素赋值
    stuArray[2].name="zhaoliu";
    stuArray[2].age =80;
    stuArray[2].score=60;

    //4. 遍历结构体数组
    for(int i=0;i<3;i++){
        cout<<"name:"<<stuArray[i].name 
        << " age:" <<stuArray[i].age
        <<" score:"<<stuArray[i].score<<endl;
    }


}
```
