# 实型 - 浮点型

&#x20;浮点型变量： 1. 单精度 float(4字节) 2. 双精度 double(8字节)

```cpp
#include <iostream>

using namespace std;

int main(){

    float f1 = 3.14f;
    
    cout << "f1 = " << f1 << endl;
    system("pause");
    
    // 统计两个占用内存空间
    
    cout << "float 占用内存空间" << sizeof(float) << endl;
    cout << "double 占用内存空间" << sizeof(double) << endl;

}
```

