# 指针的算数计算

```
ptr++
```

执行 ptr++ 后，指针 ptr 会向前移动 4 个字节，指向下一个整型元素的地址。这是由于指针算术运算会根据指针的类型和大小来决定移动的距离。在这种情况下，由于是一个 32 位整数指针，每个整数占据 4 个字节，因此 ptr++ 会将指针 ptr 向前移动 4 个字节，指向下一个整型元素的地址。

如果 ptr 指向一个地址为 1000 的字符，执行 ptr++ 指针 ptr 的值会增加，指向下一个字符元素的地址，由于 ptr 是一个字符指针，每个字符占据 1 个字节，因此 ptr++ 会将 ptr 的值增加 1，执行后 ptr 指向地址 1001。

指针算术运算的详细解析：

* 加法运算：可以对指针进行加法运算。当一个指针p加上一个整数n时，结果是指针p向前移动n个元素的大小。例如，如果p是一个int类型的指针，每个int占4个字节，那么p + 1将指向p所指向的下一个int元素。
* 减法运算：可以对指针进行减法运算。当一个指针p减去一个整数n时，结果是指针p向后移动n个元素的大小。例如，如果p是一个int类型的指针，每个int占4个字节，那么p - 1将指向p所指向的前一个int元素。
* 指针与指针之间的减法运算：可以计算两个指针之间的距离。当从一个指针p减去另一个指针q时，结果是两个指针之间的元素个数。例如，如果p和q是两个int类型的指针，每个int占4个字节，那么p - q将得到两个指针之间的元素个数。
* 指针与整数之间的比较运算：可以将指针与整数进行比较运算。可以使用关系运算符（如<、>、<=、>=）对指针和整数进行比较。这种比较通常用于判断指针是否指向某个有效的内存位置。

### 递增一个指针

我们喜欢在程序中使用指针代替数组，因为变量指针可以递增，而数组不能递增，因为数组是一个常量指针。下面的程序递增变量指针，以便顺序访问数组中的每一个元素：

<pre class="language-cpp"><code class="lang-cpp">#include &#x3C;iostream>
 
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
   int  *ptr;
 
   // 指针中的数组地址
   ptr = var;
   for (int i = 0; i &#x3C; MAX; i++)
   {
      cout &#x3C;&#x3C; "Address of var[" &#x3C;&#x3C; i &#x3C;&#x3C; "] = ";
      cout &#x3C;&#x3C; ptr &#x3C;&#x3C; endl;
 
      cout &#x3C;&#x3C; "Value of var[" &#x3C;&#x3C; i &#x3C;&#x3C; "] = ";
      cout &#x3C;&#x3C; *ptr &#x3C;&#x3C; endl;
 
      // 移动到下一个位置
      ptr++;
   }
   return 0;
}

//Address of var[0] = 0xbfa088b0
//Value of var[0] = 10
//Address of var[1] = 0xbfa088b4
//Value of var[1] = 100
<strong>//Address of var[2] = 0xbfa088b8
</strong>//Value of var[2] = 200
</code></pre>

### 递减一个指针

同样地，对指针进行递减运算，即把值减去其数据类型的字节数，如下所示：

```cpp
#include <iostream>
 
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
   int  *ptr;
 
   // 指针中最后一个元素的地址
   ptr = &var[MAX-1];
   for (int i = MAX; i > 0; i--)
   {
      cout << "Address of var[" << i << "] = ";
      cout << ptr << endl;
 
      cout << "Value of var[" << i << "] = ";
      cout << *ptr << endl;
 
      // 移动到下一个位置
      ptr--;
   }
   return 0;
}

// Address of var[3] = 0xbfdb70f8
// Value of var[3] = 200
// Address of var[2] = 0xbfdb70f4
// Value of var[2] = 100
// Address of var[1] = 0xbfdb70f0
// Value of var[1] = 10

```

### 指针的比较

指针可以用关系运算符进行比较，如 ==、< 和 >。如果 p1 和 p2 指向两个相关的变量，比如同一个数组中的不同元素，则可对 p1 和 p2 进行大小比较。

下面的程序修改了上面的实例，只要变量指针所指向的地址小于或等于数组的最后一个元素的地址 \&var\[MAX - 1]，则把变量指针进行递增：

```cpp
#include <iostream>
 
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
   int  *ptr;
 
   // 指针中第一个元素的地址
   ptr = var;
   int i = 0;
   while ( ptr <= &var[MAX - 1] )
   {
      cout << "Address of var[" << i << "] = ";
      cout << ptr << endl;
 
      cout << "Value of var[" << i << "] = ";
      cout << *ptr << endl;
 
      // 指向上一个位置
      ptr++;
      i++;
   }
   return 0;
}


// Address of var[0] = 0xbfce42d0
// Value of var[0] = 10
// Address of var[1] = 0xbfce42d4
// Value of var[1] = 100
// Address of var[2] = 0xbfce42d8
// Value of var[2] = 200

```
