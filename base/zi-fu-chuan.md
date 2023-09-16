# 字符串

### C 语言字符串

```c
char 字符串名 [] = "你好"
// 注意； 等号后面要用双引号

char site[7] = {'R', 'U', 'N', 'O', 'O', 'B', '\0'};

```

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### C++ 字符串

C++ 中有大量的函数用来操作以 null 结尾的字符串:

```cpp
#include<iostream>
using namespace std;
#include<string>

int main(){
    // C++ 字符串
    
    string str = "hello world";
    cout << str << endl;
    
}
```

<table><thead><tr><th width="101.5">序号</th><th>函数 &#x26; 目的</th></tr></thead><tbody><tr><td>1</td><td>strcpy(s1, s2);<br>复制字符串 s2 到字符串 s1。</td></tr><tr><td>2</td><td><p>strcat(s1, s2);<br>连接字符串 s2 到字符串 s1 的末尾。连接字符串也可以用 + 号，例如:<br></p><pre><code>string str1 = "runoob";
string str2 = "google";
string str = str1 + str2;
</code></pre></td></tr><tr><td>3</td><td>strlen(s1);<br>返回字符串 s1 的长度。</td></tr><tr><td>4</td><td>strcmp(s1, s2);<br>如果 s1 和 s2 是相同的，则返回 0；如果 s1&#x3C;s2 则返回值小于 0；如果 s1>s2 则返回值大于 0。</td></tr><tr><td>5</td><td>strchr(s1, ch);<br>返回一个指针，指向字符串 s1 中字符 ch 的第一次出现的位置。</td></tr><tr><td>6</td><td>strstr(s1, s2);<br>返回一个指针，指向字符串 s1 中字符串 s2 的第一次出现的位置。</td></tr></tbody></table>

