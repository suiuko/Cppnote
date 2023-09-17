# IF 语句

### IF 语句

```cpp
if(boolean_expression)
{
   // 如果布尔表达式为真将执行的语句
}
```

### IF .. ELSE 语句

```cpp
if(boolean_expression)
{
   // 如果布尔表达式为真将执行的语句
}
else
{
   // 如果布尔表达式为假将执行的语句
}
```

### IF .. ELSE IF ...ELSE语句

一个 if 语句后可跟一个可选的 else if...else 语句，这可用于测试多种条件。

当使用 if...else if...else 语句时，以下几点需要注意：

* 一个 if 后可跟零个或一个 else，else 必须在所有 else if 之后。
* 一个 if 后可跟零个或多个 else if，else if 必须在 else 之前。
* 一旦某个 else if 匹配成功，其他的 else if 或 else 将不会被测试。

```cpp
if(boolean_expression 1)
{
   // 当布尔表达式 1 为真时执行
}
else if( boolean_expression 2)
{
   // 当布尔表达式 2 为真时执行
}
else if( boolean_expression 3)
{
   // 当布尔表达式 3 为真时执行
}
else 
{
   // 当上面条件都不为真时执行
}

```

### 嵌套if语句

嵌套使用if语句，达到更精确的条件判断

