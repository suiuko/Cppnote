# 字符型

字符型变量只占用1 个字节。

```cpp
char ch = 'a';
```

#### 字符型变量对应 ASCII 编码

```cpp
cout << (int)ch << endl;
// a - 97
// A - 65
```

#### 错误

不能用双引号来创建， 只能用单引号

创建字符型变量的时候，单引号只能有一个字符
