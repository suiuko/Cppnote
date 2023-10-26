# 输入和输出

## getchar() & putchar()

getchar函数可以读取下一个可用字符，可以通过循环的方法来循环读取多个字符。

putchar可以把字符输出到屏幕上，并返回相同的字符。

```c
#include<stdio.h>

int main(){
    char ch;
    char a[1000];
    int i =0;
    while ((ch=getchar())!='\n')
    {
        // putchar(ch);
        a[i] = ch;
        i++;
    }
    for(int y =0;a[y]!= '\0';y++){
        printf("%c",a[y]);
    }
    printf("\n");
    return 0;
}
```

## gets() & puts()函数

char \*gets(char \*s) 函数从 stdin 读取一行到 s 所指向的缓冲区，直到一个终止符或 EOF。

int puts(const char \*s) 函数把字符串 s 和一个尾随的换行符写入到 stdout。

当上面的代码被编译和执行时，它会等待您输入一些文本，当您输入一个文本并按下回车键时，程序会继续并读取一整行直到该行结束

## scanf() 和 printf() 函数

int scanf(const char \*format, ...) 函数从标准输入流 stdin 读取输入，并根据提供的 format 来浏览输入。

int printf(const char \*format, ...) 函数把输出写入到标准输出流 stdout ，并根据提供的格式产生输出。

format 可以是一个简单的常量字符串，但是您可以分别指定 %s、%d、%c、%f 等来输出或读取字符串、整数、字符或浮点数。还有许多其他可用的格式选项
