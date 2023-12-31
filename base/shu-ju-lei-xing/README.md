# 数据类型

## 一、基本内置类型

### 1.1 算术类型

| 类型   | 关键字      |
| ---- | -------- |
| 布尔型  | bool     |
| 字符型  | char     |
| 整型   | int      |
| 浮点型  | float    |
| 双浮点型 | double   |
| 无类型  | void     |
| 宽字符型 | wchar\_t |

可寻址的最小内存块称为字节(byte)

1 字节=8 位 bit

64 位的系统中，8 字节=64bit

#### 1.1.1 带符号类型和无符号类型

带符号能表示正负，无符号类型只能表示大于等于0 的值

| 类型                 | 位         | 范围                                                     |
| ------------------ | --------- | ------------------------------------------------------ |
| char               | 1 个字节     | -128 到 127 或者 0 到 255                                  |
| unsigned char      | 1 个字节     | 0 到 255                                                |
| signed char        | 1 个字节     | -128 到 127                                             |
| int                | 4 个字节     | -2147483648 到 2147483647                               |
| unsigned int       | 4 个字节     | 0 到 4294967295                                         |
| signed int         | 4 个字节     | -2147483648 到 2147483647                               |
| short int          | 2 个字节     | -32768 到 32767                                         |
| unsigned short int | 2 个字节     | 0 到 65,535                                             |
| signed short int   | 2 个字节     | -32768 到 32767                                         |
| long int           | 8 个字节     | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 |
| signed long int    | 8 个字节     | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 |
| unsigned long int  | 8 个字节     | 0 到 18,446,744,073,709,551,615                         |
| float              | 4 个字节     | 精度型占4个字节（32位）内存空间，+/- 3.4e +/- 38 (\~7 个数字)            |
| double             | 8 个字节     | 双精度型占8 个字节（64位）内存空间，+/- 1.7e +/- 308 (\~15 个数字)        |
| long double        | 16 个字节    | 长双精度型 16 个字节（128位）内存空间，可提供18-19位有效数字。                  |
| wchar\_t           | 2 或 4 个字节 | 1 个宽字符                                                 |

<figure><img src="../../.gitbook/assets/32-64.jpg" alt=""><figcaption></figcaption></figure>

## 二、 enumeration 枚举类型

```cpp
enum 枚举名{ 
     标识符[=整型常数], 
     标识符[=整型常数], 
... 
    标识符[=整型常数]
} 枚举变量;
```

如果枚举没有初始化, 即省掉"=整型常数"时, 则从第一个标识符开始。

例如，下面的代码定义了一个颜色枚举，变量 c 的类型为 color。最后，c 被赋值为 "blue"。

```cpp
enum color { red, green, blue } c;
c = blue;
```

默认情况下，第一个名称的值为 0，第二个名称的值为 1，第三个名称的值为 2，以此类推。但是，您也可以给名称赋予一个特殊的值，只需要添加一个初始值即可。例如，在下面的枚举中，green 的值为 5。

```cpp
enum color {red, green=5, blue };

// red = 0; green = 5; blue =6
```

## 三、 typedef 声明

您可以使用typedef 为一个已有的类型取一个新的名字。

```cpp
typedef type newname;

typedef int feet; // 告诉编译器 feet 是 int 的另一个名称
```

## 四、类型转换

### 1. 静态转换

静态转换是将一种数据类型的值强制转换为另一种数据类型的值。

静态转换通常用于比较类型相似的对象之间的转换，例如将 int 类型转换为 float 类型

不做类型检查会出现运行错误

```cpp
int i = 10;
float f = static_cast<float>(i);
std::cout << i << endl;
std::cout << sizeof(i) << endl;

>>>
10
4
```

### 2. 动态转换

动态转换通常用于将一个基类指针或引用转换为派生类指针或引用。动态转换在运行时进行类型检查，如果不能进行转换则返回空指针或引发异常

```cpp
class Base {};
class Derived : public Base {};
Base* ptr_base = new Derived;
Derived* ptr_derived = dynamic_cast<Derived*>(ptr_base); // 将基类指针转换为派生类指针
```

### 3. 常量转换

常量转换用于将 const 类型的对象转换为非 const 类型的对象。

常量转换只能用于转换掉 const 属性，不能改变对象的类型

```cpp
const int i = 10;
int& r = const_cast<int&>(i); // 常量转换，将const int转换为int
```

### 4. 重新解释转换

重新解释转换将一个数据类型的值重新解释为另一个数据类型的值，通常用于在不同的数据类型之间进行转换。

重新解释转换不进行任何类型检查，因此可能会导致未定义的行为。

```cpp
int i = 10;
float f = reinterpret_cast<float&>(i); // 重新解释将int类型转换为float类型
```
