# do - while

与while 的区别在于 do..while **会先执行一次循环语句**， 再判断循环条件

```cpp
do{
    循环语句
}while(循环条件);
```

```cpp
#include<iostream>

using namespace std;

int main(){

    //do while 语句

    int num =0;
    do{
        cout << num << endl;

        num++;
    }while(num<10);


    system("pause");

    return 0;
}
```

### 水仙花数

获取个位：对数字取模于 10

获取十位：先整除于 10，得到两位数，然后再取模与 10

获取百位：直接除以 100

判断： 个位^3+十位^3+百位^3 = 本身

```cpp
 int num = 100;
    do{
        

        int a =0; //个
        int b=0; //十
        int c=0; //百
        a = num %10;
        b = num /10 % 10;
        c = num /100;

        if(a*a*a + b*b*b +c*c*c == num){// 如果是才打印

            cout << num << endl;
        }
        
        num++;
    }while(num<1000);
    
    
//153
//370
//371
//407
```

