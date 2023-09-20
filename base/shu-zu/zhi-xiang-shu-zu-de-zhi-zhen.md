# 指向数组的指针

数组名是指向数组中第一个元素的常量指针。因此，在下面的声明中：

```cpp
double runoobAarray[50];
```

runoobAarray 是一个指向 \&runoobAarray\[0] 的指针，即数组 runoobAarray 的第一个元素的地址。因此，下面的程序片段把 p 赋值为 runoobAarray 的第一个元素的地址：

```cpp
double *p;
double runoobAarray[10];

p = runoobAarray;
```

使用数组名作为常量指针是合法的，反之亦然。因此，\*(runoobAarray + 4) 是一种访问 runoobAarray\[4] 数据的合法方式。

一旦您把第一个元素的地址存储在 p 中，您就可以使用 \*p、\*(p+1)、\*(p+2) 等来访问数组元素。
