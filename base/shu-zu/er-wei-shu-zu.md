# 二维数组

### 定义方式

1. 数据类型 数组名 \[行数]\[列数];
2. 数据类型 数组名 \[行数]\[列数] = \{{数据 1, 数据 2},{数据 3,数据 4\}};
3. 数据类型 数组名 \[行数]\[列数] = {数据 1, 数据 2,数据 3,数据 4};
4. 数据类型 数组名 \[]\[列数] = {数据 1, 数据 2,数据 3,数据 4};

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

int main(){

    // 二维数组

    //1. 数据类型 数组名[行数][列数];
    int arr[2][3];
    arr[0][0] = 1;
    arr[0][1] = 2;
    arr[0][2] = 3;
    arr[1][0] = 4;
    arr[1][1] = 5;
    arr[1][2] = 6;
    // cout << arr[0][0] <<endl;
    for(int i=0;i<2;i++){
        for(int j=0;j<3;j++){
            cout << arr[i][j] << endl;
        }
    }


    //2.数据类型 数组名 [行数][列数] = {{数据 1, 数据 2},{数据 3,数据 4}};
    int arr2[2][3]={
        {1,2,3},
        {4,5,6}
    };
    for(int i=0;i<2;i++){
        for(int j=0;j<3;j++){
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }
}
```

### 二维数组数组名

查看二维数组所占内存空间

获取二维数组首地址

```cpp
cout << "行数：" << sizeof(arr) / sizeof(arr[0]) << endl;
cout << "列数：" << sizeof(arr[0]) / sizeof(arr[0][0]) << endl;
```

### 应用案例

考试成绩统计：&#x20;

案例描述： 有三名同学（张三，李四，王五），分别输出三名同学的总成绩



<table><thead><tr><th width="163">姓名</th><th width="152">语文</th><th width="170">数学</th><th>英语</th></tr></thead><tbody><tr><td>张三</td><td>100</td><td>100</td><td>100</td></tr><tr><td>李四</td><td>90</td><td>50</td><td>100</td></tr><tr><td>王五</td><td>60</td><td>70</td><td>80</td></tr></tbody></table>

```cpp
#include<iostream>
#include<string>
using namespace std;

int main(){

    //应用案例

    //1. 创建二维数组
    int scores[3][3] = {
        {100,100,100},
        {90,50,100},
        {60,70,80}
    };

    string names[3] = {"张三","李四","王五"};
    //2.统计每个人总和分数
    
    for(int i =0;i<3;i++){
        int sum = 0; //总计分数总和
        for(int j=0;j<3;j++){
            sum +=scores[i][j];
            // cout << scores[i][j] << " ";
        }
        cout <<  names[i] << "的总分为："<< sum << endl;
    }
}
```
