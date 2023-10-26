# 常量

## 整数/浮点常量

## 字符常量

<table><thead><tr><th width="222.5">转义序列</th><th>含义</th></tr></thead><tbody><tr><td>\\</td><td>\ 字符</td></tr><tr><td>\'</td><td>' 字符</td></tr><tr><td>\"</td><td>" 字符</td></tr><tr><td>\?</td><td>? 字符</td></tr><tr><td>\a</td><td>警报铃声</td></tr><tr><td>\b</td><td>退格键</td></tr><tr><td>\f</td><td>换页符</td></tr><tr><td>'\n'</td><td>换行符</td></tr><tr><td>'\r'</td><td>回车</td></tr><tr><td>'\t'</td><td>水平制表符</td></tr><tr><td>\v</td><td>垂直制表符</td></tr><tr><td>\ooo</td><td>一到三位的八进制数</td></tr><tr><td>\xhh . . .</td><td>一个或多个数字的十六进制数</td></tr></tbody></table>

## 定义常量

在 C 中，有两种简单的定义常量的方式：

1. 使用 #define 预处理器： #define 可以在程序中定义一个常量，它在编译时会被替换为其对应的值。
2. 使用 const 关键字：const 关键字用于声明一个只读变量，即该变量的值不能在程序运行时修改

### define 预处理器

```c
#define 常量名 常量值
#define PI 3.14159
```

### const 关键字

```c
const 数据类型 常量名 = 常量值;
const int MAX_VALUE = 100;
```
