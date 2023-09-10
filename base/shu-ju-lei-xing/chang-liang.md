# 常量

### 1. 定义常量方式

1. &#x20;`#define 宏常量: define 常量名 常量值`
2. &#x20;`const修饰的变量：const 数据类型 变量名 = 常量值`

<pre class="language-cpp"><code class="lang-cpp"><strong>#include &#x3C;stdio.h>
</strong>#include &#x3C;iostream>

using namespace std;

// 1. #define 宏常量

# define Day 7

int main(){

    cout &#x3C;&#x3C; "一周一共有：" &#x3C;&#x3C; Day &#x3C;&#x3C; "天" &#x3C;&#x3C; endl;

    //2. const 修饰的变量
    int month  = 12;  
    const int month1 = 12; // const 修饰的也是常量

    cout &#x3C;&#x3C; "一年有" &#x3C;&#x3C; month &#x3C;&#x3C; "月" &#x3C;&#x3C; endl; 


    system("pause");

    return 0;
}
</code></pre>

