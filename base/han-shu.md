# 函数

### 定义函数

一般格式：

```cpp
return_type fuction_name(parameter list{
    body of the function
}
```

返回类型：一个函数可以返回一个值，return\_type 是函数返回的值的数据类型；如果不需要返回 用void

函数名称：这是函数的实际名称。

参数：需要 调用的实际参数

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

### 参数调用

如果函数要使用参数，则必须声明接受参数值的变量。这些变量称为函数的形式参数。

形式参数就像函数内的其他局部变量，在进入函数时被创建，退出函数时被销毁。

当调用函数时，有三种向函数传递参数的方式：

| 调用类型                                                                         | 描述                                                           |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [传值调用](https://www.runoob.com/cplusplus/cpp-function-call-by-value.html)     | 该方法把参数的实际值赋值给函数的形式参数。在这种情况下，修改函数内的形式参数对实际参数没有影响。             |
| [指针调用](https://www.runoob.com/cplusplus/cpp-function-call-by-pointer.html)   | 该方法把参数的地址赋值给形式参数。在函数内，该地址用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |
| [引用调用](https://www.runoob.com/cplusplus/cpp-function-call-by-reference.html) | 该方法把参数的引用赋值给形式参数。在函数内，该引用用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |

#### 传值调用

向函数传递参数的传值调用方法，把参数的实际值复制给函数的形式参数。在这种情况下，修改函数内的形式参数不会影响实际参数。

默认情况下，C++ 使用_传值调用_方法来传递参数。一般来说，这意味着函数内的代码不会改变用于调用函数的实际参数。函数 swap() 定义如下：

```cpp
// 函数定义
void swap(int x, int y)
{
   int temp;
 
   temp = x; /* 保存 x 的值 */
   x = y;    /* 把 y 赋值给 x */
   y = temp; /* 把 x 赋值给 y */
  
   return;
}
```

#### 指针调用

向函数传递参数的指针调用方法，把参数的地址复制给形式参数。在函数内，该地址用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。

按指针传递值，参数指针被传递给函数，就像传递其他值给函数一样。因此相应地，在下面的函数 swap() 中，您需要声明函数参数为指针类型，该函数用于交换参数所指向的两个整数变量的值。

```cpp
// 函数定义
void swap(int *x, int *y)
{
   int temp;
   temp = *x;    /* 保存地址 x 的值 */
   *x = *y;        /* 把 y 赋值给 x */
   *y = temp;    /* 把 x 赋值给 y */
  
   return;
}

```

```cpp
#include <iostream>
using namespace std;

// 函数声明
void swap(int *x, int *y);

int main ()
{
   // 局部变量声明
   int a = 100;
   int b = 200;
 
   cout << "交换前，a 的值：" << a << endl;
   cout << "交换前，b 的值：" << b << endl;

   /* 调用函数来交换值
    * &a 表示指向 a 的指针，即变量 a 的地址 
    * &b 表示指向 b 的指针，即变量 b 的地址 
    */
   swap(&a, &b);

   cout << "交换后，a 的值：" << a << endl;
   cout << "交换后，b 的值：" << b << endl;
 
   return 0;
}

```

### 引用调用

向函数传递参数的引用调用方法，把引用的地址复制给形式参数。在函数内，该引用用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。

按引用传递值，参数引用被传递给函数，就像传递其他值给函数一样。因此相应地，在下面的函数 swap() 中，您需要声明函数参数为引用类型，该函数用于交换参数所指向的两个整数变量的值。

```cpp
// 函数定义
void swap(int &x, int &y)
{
   int temp;
   temp = x; /* 保存地址 x 的值 */
   x = y;    /* 把 y 赋值给 x */
   y = temp; /* 把 x 赋值给 y  */
  
   return;
}

```

### Lambda 函数与表达式

C++11 提供了对匿名函数的支持,称为 Lambda 函数(也叫 Lambda 表达式)。

Lambda 表达式把函数看作对象。Lambda 表达式可以像对象一样使用，比如可以将它们赋给变量和作为参数传递，还可以像函数一样对其求值。

Lambda 表达式本质上与函数声明非常类似。Lambda 表达式具体形式如下:

```
[capture](parameters)->return-type{body}
```

例如：

```
[](int x, int y){ return x < y ; }
```

如果没有返回值可以表示为：

```
[capture](parameters){body}
```

例如：

```
[]{ ++global_x; } 
```

在一个更为复杂的例子中，返回类型可以被明确的指定如下：

```
[](int x, int y) -> int { int z = x + y; return z + x; }
```

本例中，一个临时的参数 z 被创建用来存储中间结果。如同一般的函数，z 的值不会保留到下一次该不具名函数再次被调用时。

如果 lambda 函数没有传回值（例如 void），其返回类型可被完全忽略。

在Lambda表达式内可以访问当前作用域的变量，这是Lambda表达式的闭包（Closure）行为。 与JavaScript闭包不同，C++变量传递有传值和传引用的区别。可以通过前面的\[]来指定：

```
[]      // 沒有定义任何变量。使用未定义变量会引发错误。
[x, &y] // x以传值方式传入（默认），y以引用方式传入。
[&]     // 任何被使用到的外部变量都隐式地以引用方式加以引用。
[=]     // 任何被使用到的外部变量都隐式地以传值方式加以引用。
[&, x]  // x显式地以传值方式加以引用。其余变量以引用方式加以引用。
[=, &z] // z显式地以引用方式加以引用。其余变量以传值方式加以引用。
```

另外有一点需要注意。对于\[=]或\[&]的形式，lambda 表达式可以直接使用 this 指针。但是，对于\[]的形式，如果要使用 this 指针，必须显式传入：

```
[this]() { this->someFunc(); }();
```
