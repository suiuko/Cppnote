# 变量类型

| 类型       | 描述                                                                                                                                                                                                         |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| bool     | 布尔类型，存储值 true 或 false，占用 1 个字节。                                                                                                                                                                            |
| char     | 字符类型，用于存储 ASCII 字符，通常占用 1 个字节。                                                                                                                                                                             |
| int      | 整数类型，通常用于存储普通整数，通常占用 4 个字节。                                                                                                                                                                                |
| float    | <p>单精度浮点值，用于存储单精度浮点数。单精度是这样的格式，1 位符号，8 位指数，23 位小数，通常占用4个字节。</p><p><img src="https://www.runoob.com/wp-content/uploads/2014/09/v2-749cc641eb4d5dafd085e8c23f8826aa_hd.png" alt="" data-size="original"></p> |
| double   | <p>双精度浮点值，用于存储双精度浮点数。双精度是 1 位符号，11 位指数，52 位小数，通常占用 8 个字节。</p><p><img src="https://www.runoob.com/wp-content/uploads/2014/09/v2-48240f0e1e0dd33ec89100cbe2d30707_hd.png" alt="" data-size="original"></p>   |
| void     | 表示类型的缺失。                                                                                                                                                                                                   |
| wchar\_t | 宽字符类型，用于存储更大范围的字符，通常占用 2 个或 4 个字节                                                                                                                                                                          |

1. 整数类型（Integer Types）：
   * `int`：用于表示整数，通常占用4个字节。
   * `short`：用于表示短整数，通常占用2个字节。
   * `long`：用于表示长整数，通常占用4个字节。
   * `long long`：用于表示更长的整数，通常占用8个字节。
2. 浮点类型（Floating-Point Types）：
   * `float`：用于表示单精度浮点数，通常占用4个字节。
   * `double`：用于表示双精度浮点数，通常占用8个字节。
   * `long double`：用于表示更高精度的浮点数，占用字节数可以根据实现而变化。
3. 字符类型（Character Types）：
   * `char`：用于表示字符，通常占用1个字节。
   * `wchar_t`：用于表示宽字符，通常占用2或4个字节。
   * `char16_t`：用于表示16位Unicode字符，占用2个字节。
   * `char32_t`：用于表示32位Unicode字符，占用4个字节。
4. 布尔类型（Boolean Type）：
   * `bool`：用于表示布尔值，只能取`true`或`false`。
5. 枚举类型（Enumeration Types）：
   * `enum`：用于定义一组命名的整数常量。
6. 指针类型（Pointer Types）：
   * `type*`：用于表示指向类型为`type`的对象的指针。
7. 数组类型（Array Types）：
   * `type[]`或`type[size]`：用于表示具有相同类型的元素组成的数组。
8. 结构体类型（Structure Types）：
   * `struct`：用于定义包含多个不同类型成员的结构。
9. 类类型（Class Types）：
   * `class`：用于定义具有属性和方法的自定义类型。
10. 共用体类型（Union Types）：
    * `union`：用于定义一种特殊的数据类型，它可以在相同的内存位置存储不同的数据类型

short 2 < int 4<= long < long long&#x20;

## c++中变量的声明

使用 extern 关键字在任何地方声明一个变量，但变量只能在某个文件、函数或代码块中被定义一次

```cpp
#include <iostream>
using namespace std;
 
// 变量声明
extern int a, b;
extern int c;
extern float f;
  
int main ()
{
  // 变量定义
  int a, b;
  int c;
  float f;
 
  // 实际初始化
  a = 10;
  b = 20;
  c = a + b;
 
  cout << c << endl ;
 
  f = 70.0/3.0;
  cout << f << endl ;
 
  return 0;
}

>>>30
>>>23.3333
```
