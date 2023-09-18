# while

```cpp
while(循环条件){
    循环体
}
//只要循环条件结果为真，就执行循环语句
//https://raw.githubusercontent.com/ermaozi/get_subscribe/main/subscribe/clash.yml
```

```cpp
int num = 0;

while(num<10){
    cout << num << endl;
    num++;
}
//while(true) 则会进入死循环

```

猜数字

```cpp
#include<iostream>
using namespace std;
// time 系统时间头文件
#include<ctime>

int main(){

    //添加随机数的种子，用当前系统的时间生成随机数，每次都不一样
    
    srand((unsigned int)time(NULL))
    // 1.生成随机数
    rand()%100 // rand()%100+1 生成 0+1 ~ 99+1的随机数
    
    cout << num << endl;
    
    //2. 玩家进行检测
    int val =0; // 玩家输入的数据
    
    
    while(){
       cin >> val; 
    //3. 判断玩家的猜测
    
        if(val > num){
            cout << "猜测过大" << endl;
        }
        else if (val < num)
        {
            cout << "猜测过小" << endl;
        }
        else 
        {    //猜对了 退出
            cout << "恭喜您 猜对了" << endl;
            break; // 用该关键词 可以退出循环
        }
    }
    
    
    
    
}
```
