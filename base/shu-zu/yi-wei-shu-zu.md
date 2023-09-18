# 一维数组

## 一维数组定义的三种方式：

1. 数据类型 数组名\[数组长度];
2. 数据类型 数组名\[数组长度] = {值1,值2 ...};
3. 数据类型 数组名\[] = {值1,值2 ...};

### 数组的特点

放在一块连续的内存空间中，数组中的每个元素都是相同数据类型

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

我们可以通过下标来访问数组中的元素

### 一维数组名称用途

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

```cpp
#include<iostream>

using namespace std;

int main(){

    //数组

    // 1. 数据类型 数组名[数组长度];
    int arr[5];

    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;
    arr[3] = 40;
    arr[4] = 50;

    cout << arr[0] << endl;

    //2. 数据类型 数组名[数组长度] = {1,2}
    int arr2[5] = {1,2,3,4,5};

    for(int i =0;i<5;i++){
        cout << arr2[i] << endl;
    }

    // 3. 数据类型 数组名[]={值1,值2 }
    int arr3[]={9,8,7,6,5,4,3,2,1};
    for(int i =0;i<9;i++){
        cout<< arr3[i]<<endl;
    }
}
```

### 练习案例 - 找最大值

```cpp
#include<iostream>

using namespace std;

int main(){

   

    int arr[5] = {300,350,200,400,250};
    // 找最大值
    int max = 0;
    for(int i = 0; i<5;i++){
        //更新最大值
        if(arr[i]>max){
            max = arr[i];
        }
    }
    cout << max << endl;
    
}
```

### 数组逆置

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

