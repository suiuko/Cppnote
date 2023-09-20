# 从函数返回数组

C++ 不允许返回一个完整的数组作为函数的参数。但是，您可以通过指定不带索引的数组名来返回一个指向数组的指针。

如果您想要从函数返回一个一维数组，您必须声明一个返回指针的函数，如下：

```cpp
int *myFunction(){
    // ...
}
```

```cpp
int *myFunction(){

    int myArray[3] = {1,2,3};
    return myArray;
}
```

**注意：**你不能简单地返回指向局部数组的指针，因为当函数结束时，局部数组将被销毁，指向它的指针将变得无效。

C++ 不支持在函数外返回局部变量的地址，除非定义局部变量为 static 变量。

为了避免以上情况，你可以使用静态数组或者动态分配数组。

使用静态数组需要在函数内部创建一个静态数组，并将其地址返回，例如：

```cpp
int* myFunction()
{
   static int myArray[3] = {1, 2, 3};
   return myArray;
}
```

#### 练习

现在，让我们来看下面的函数，它会生成 10 个随机数，并使用数组来返回它们，具体如下：

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>
 
using namespace std;
 
// 要生成和返回随机数的函数
int * getRandom( )
{
  static int  r[10];
 
  // 设置种子
  srand( (unsigned)time( NULL ) );
  for (int i = 0; i < 10; ++i)
  {
    r[i] = rand();
    cout << r[i] << endl;
  }
 
  return r;
}
 
// 要调用上面定义函数的主函数
int main ()
{
   // 一个指向整数的指针
   int *p;
 
   p = getRandom();
   for ( int i = 0; i < 10; i++ )
   {
       cout << "*(p + " << i << ") : ";
       cout << *(p + i) << endl;
   }
 
   return 0;
}
```
