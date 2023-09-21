# 函数

### 定义函数

一般格式：

```cpp
return_type fuction_name(parameter list){
    body of the function
}

返回值类型 函数名(参数列表){
    函数题语句
    return 表达式

}
```

返回类型：一个函数可以返回一个值，return\_type 是函数返回的值的数据类型；如果不需要返回 用void

函数名称：这是函数的实际名称。

参数：需要 调用的实际参数

### 函数定义步骤

1. 返回值类型
2. 函数名
3. 参数表列
4. 函数体语句
5. return 表达式

#### 实例

```cpp
int max(int num1, int num2){

    //局部变量声明
    int result;
    if(num1 > num2)
        result = num1;
    else
        result = num2;
        
    return result;
}
```

### 函数声明

函数声明会告诉编译器函数的名称及如何调用函数，函数的实际主体可以单独定义。

### 调用函数

```cpp
#include <iostream>
using namespace std;
 
// 函数声明
int max(int num1, int num2);
 
int main ()
{
   // 局部变量声明
   int a = 100;
   int b = 200;
   int ret;
 
   // 调用函数来获取最大值
   ret = max(a, b);
 
   cout << "Max value is : " << ret << endl;
 
   return 0;
}
 
// 函数返回两个数中较大的那个数
int max(int num1, int num2) 
{
   // 局部变量声明
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```

###
