# for

```cpp
for(起始表达式;条件表达式;末尾循环体){
    循环语句;
}
```

### 敲桌子案例

逢 7 过

```cpp
#include<iostream>

using namespace std;

int main(){
    //先输出 1-100 数字

    for(int i =1;i<=100;i++){

        //从 100 个数字中找到特殊的数字
        //如果是 7 的背书，个位有 7，十位有 7，打印出来

        if(i%7 ==0|| i%10 ==7 || i/10 ==7)
        {
            cout << "7！过" << endl;
        }
        else {
            //如果不是特殊数字，才打印

            cout << i << endl;

        }
    }


}
```
