# 运算符

### 算术运算符

<table><thead><tr><th width="123.33333333333334">运算符</th><th width="244">描述</th><th>实例</th></tr></thead><tbody><tr><td>+</td><td>把两个操作数相加</td><td>A + B 将得到 30</td></tr><tr><td>-</td><td>从第一个操作数中减去第二个操作数</td><td>A - B 将得到 -10</td></tr><tr><td>*</td><td>把两个操作数相乘</td><td>A * B 将得到 200</td></tr><tr><td>/</td><td>分子除以分母</td><td>B / A 将得到 2</td></tr><tr><td>%</td><td>取模运算符，整除后的余数</td><td>B % A 将得到 0</td></tr><tr><td>++</td><td><a href="https://www.runoob.com/cplusplus/cpp-increment-decrement-operators.html">自增运算符</a>，整数值增加 1</td><td>A++ 将得到 11</td></tr><tr><td>--</td><td><a href="https://www.runoob.com/cplusplus/cpp-increment-decrement-operators.html">自减运算符</a>，整数值减少 1</td><td>A-- 将得到 9</td></tr></tbody></table>

```cpp
#include<iostream>
using namespace std;

int main(){

    
    int a1 = 10;
    int b1 = 3;

    cout << a1 + b1 << endl;
    cout << a1 - b1 << endl;
    cout << a1 * b1 << endl;
    cout << a1 / b1 << endl;

    // 两个小数可以相除
    double d1 = 0.5;
    double d2 = 0.25;
    cout << d1 / d2 << endl;

    // 取模 %
    // 取模运算就是求余数
    // 两个小数是不能取模
    
    int c1 = 10;
    int e1 = 3;
    cout << c1 % e1 << endl;

}
```

```cpp
//前置递增
先让变量+1 然后进行表达式的运算
//后置递增
先进行表达式运算，后让变量+1

```

### 赋值运算符

<table><thead><tr><th width="116.33333333333334">运算符</th><th>描述</th><th>实例</th></tr></thead><tbody><tr><td>=</td><td>简单的赋值运算符，把右边操作数的值赋给左边操作数</td><td>C = A + B 将把 A + B 的值赋给 C</td></tr><tr><td>+=</td><td>加且赋值运算符，把右边操作数加上左边操作数的结果赋值给左边操作数</td><td>C += A 相当于 C = C + A</td></tr><tr><td>-=</td><td>减且赋值运算符，把左边操作数减去右边操作数的结果赋值给左边操作数</td><td>C -= A 相当于 C = C - A</td></tr><tr><td>*=</td><td>乘且赋值运算符，把右边操作数乘以左边操作数的结果赋值给左边操作数</td><td>C *= A 相当于 C = C * A</td></tr><tr><td>/=</td><td>除且赋值运算符，把左边操作数除以右边操作数的结果赋值给左边操作数</td><td>C /= A 相当于 C = C / A</td></tr><tr><td>%=</td><td>求模且赋值运算符，求两个操作数的模赋值给左边操作数</td><td>C %= A 相当于 C = C % A</td></tr><tr><td>&#x3C;&#x3C;=</td><td>左移且赋值运算符</td><td>C &#x3C;&#x3C;= 2 等同于 C = C &#x3C;&#x3C; 2</td></tr><tr><td>>>=</td><td>右移且赋值运算符</td><td>C >>= 2 等同于 C = C >> 2</td></tr><tr><td>&#x26;=</td><td>按位与且赋值运算符</td><td>C &#x26;= 2 等同于 C = C &#x26; 2</td></tr><tr><td>^=</td><td>按位异或且赋值运算符</td><td>C ^= 2 等同于 C = C ^ 2</td></tr><tr><td>|=</td><td>按位或且赋值运算符</td><td>C |= 2 等同于 C = C | 2</td></tr></tbody></table>

### 关系运算符

假设变量 A 的值为 10，变量 B 的值为 20，则：

<table><thead><tr><th width="142.33333333333334">运算符</th><th>描述</th><th>实例</th></tr></thead><tbody><tr><td>==</td><td>检查两个操作数的值是否相等，如果相等则条件为真。</td><td>(A == B) 不为真。</td></tr><tr><td>!=</td><td>检查两个操作数的值是否相等，如果不相等则条件为真。</td><td>(A != B) 为真。</td></tr><tr><td>></td><td>检查左操作数的值是否大于右操作数的值，如果是则条件为真。</td><td>(A > B) 不为真。</td></tr><tr><td>&#x3C;</td><td>检查左操作数的值是否小于右操作数的值，如果是则条件为真。</td><td>(A &#x3C; B) 为真。</td></tr><tr><td>>=</td><td>检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。</td><td>(A >= B) 不为真。</td></tr><tr><td>&#x3C;=</td><td>检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。</td><td>(A &#x3C;= B) 为真。</td></tr></tbody></table>

### 逻辑运算符

假设变量 A 的值为 1，变量 B 的值为 0，则：

<table><thead><tr><th width="97.33333333333334">运算符</th><th>描述</th><th>实例</th></tr></thead><tbody><tr><td>&#x26;&#x26;</td><td>称为逻辑与运算符。如果两个操作数都 true，则条件为 true。</td><td>(A &#x26;&#x26; B) 为 false。</td></tr><tr><td>||</td><td>称为逻辑或运算符。如果两个操作数中有任意一个 true，则条件为 true。</td><td>(A || B) 为 true。</td></tr><tr><td>!</td><td>称为逻辑非运算符。用来逆转操作数的逻辑状态，如果条件为 true 则逻辑非运算符将使其为 false。</td><td>!(A &#x26;&#x26; B) 为 true。</td></tr></tbody></table>

### 位运算符

<table><thead><tr><th width="103">p</th><th width="124">q</th><th width="103">p &#x26; q</th><th width="122">p | q</th><th>p ^ q</th></tr></thead><tbody><tr><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>0</td><td>1</td><td>0</td><td>1</td><td>1</td></tr><tr><td>1</td><td>1</td><td>1</td><td>1</td><td>0</td></tr><tr><td>1</td><td>0</td><td>0</td><td>1</td><td>1</td></tr></tbody></table>

下表显示了 C++ 支持的位运算符。假设变量 A 的值为 60，变量 B 的值为 13，则：

<table><thead><tr><th width="125.33333333333334">运算符</th><th>描述</th><th>实例</th></tr></thead><tbody><tr><td>&#x26;</td><td><p>按位与操作，按二进制位进行"与"运算。运算规则：</p><pre><code>0&#x26;0=0;   
0&#x26;1=0;    
1&#x26;0=0;     
1&#x26;1=1;
</code></pre></td><td>(A &#x26; B) 将得到 12，即为 0000 1100</td></tr><tr><td>|</td><td><p>按位或运算符，按二进制位进行"或"运算。运算规则：</p><pre><code>0|0=0;   
0|1=1;   
1|0=1;    
1|1=1;
</code></pre></td><td>(A | B) 将得到 61，即为 0011 1101</td></tr><tr><td>^</td><td><p>异或运算符，按二进制位进行"异或"运算。运算规则：</p><pre><code>0^0=0;   
0^1=1;   
1^0=1;  
1^1=0;
</code></pre></td><td>(A ^ B) 将得到 49，即为 0011 0001</td></tr><tr><td>~</td><td><p>取反运算符，按二进制位进行"取反"运算。运算规则：</p><pre><code>~1=-2;   
~0=-1;
</code></pre></td><td>(~A ) 将得到 -61，即为 1100 0011，一个有符号二进制数的补码形式。</td></tr><tr><td>&#x3C;&#x3C;</td><td>二进制左移运算符。将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）。</td><td>A &#x3C;&#x3C; 2 将得到 240，即为 1111 0000</td></tr><tr><td>>></td><td>二进制右移运算符。将一个数的各二进制位全部右移若干位，正数左补0，负数左补1，右边丢弃。</td><td>A >> 2 将得到 15，即为 0000 1111</td></tr></tbody></table>

### 杂项运算符

下表列出了 C++ 支持的其他一些重要的运算符。

| 运算符               | 描述                                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------------- |
| sizeof            | [sizeof 运算符](https://www.runoob.com/cplusplus/cpp-sizeof-operator.html)返回变量的大小。例如，sizeof(a) 将返回 4，其中 a 是整数。   |
| Condition ? X : Y | [条件运算符](https://www.runoob.com/cplusplus/cpp-conditional-operator.html)。如果 Condition 为真 ? 则值为 X : 否则值为 Y。     |
| ,                 | [逗号运算符](https://www.runoob.com/cplusplus/cpp-comma-operator.html)会顺序执行一系列运算。整个逗号表达式的值是以逗号分隔的列表中的最后一个表达式的值。    |
| .（点）和 ->（箭头）      | [成员运算符](https://www.runoob.com/cplusplus/cpp-member-operators.html)用于引用类、结构和共用体的成员。                           |
| Cast              | [强制转换运算符](https://www.runoob.com/cplusplus/cpp-casting-operators.html)把一种数据类型转换为另一种数据类型。例如，int(2.2000) 将返回 2。 |
| &                 | [指针运算符 &](https://www.runoob.com/cplusplus/cpp-pointer-operators.html) 返回变量的地址。例如 \&a; 将给出变量的实际地址。            |
| \*                | [指针运算符 \*](https://www.runoob.com/cplusplus/cpp-pointer-operators.html) 指向一个变量。例如，\*var; 将指向变量 var。           |

### C++ 中的运算符优先级

| 类别       | 运算符                                 | 结合性   |
| -------- | ----------------------------------- | ----- |
| 后缀       | () \[] -> . ++ - -                  | 从左到右  |
| 一元       | + - ! \~ ++ - - (type)\* & sizeof   | 从右到左  |
| 乘除       | \* / %                              | 从左到右  |
| 加减       | + -                                 | 从左到右  |
| 移位       | << >>                               | 从左到右  |
| 关系       | < <= > >=                           | 从左到右  |
| 相等       | == !=                               | 从左到右  |
| 位与 AND   | &                                   | 从左到右  |
| 位异或 XOR  | ^                                   | 从左到右  |
| 位或 OR    | \|                                  | 从左到右  |
| 逻辑与 AND  | &&                                  | 从左到右  |
| 逻辑或 OR   | \|\|                                | 从左到右  |
| 条件       | ?:                                  | 从右到左  |
| 赋值       | = += -= \*= /= %=>>= <<= &= ^= \|=  | 从右到左  |
| 逗号       | ,                                   | 从左到右  |
