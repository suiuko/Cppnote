# 排序

### 冒泡排序

比较相邻的元素，如果第一个比第二个大，就交换他们两个。

对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大的值

重复以上的步骤，每次比较次数-1，直到不比较

#### 示例：将数组{4,2,8,0,5,7,1,3,9}进行升序排序

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

排序的总轮数 = 元素的个数 -1&#x20;

每轮对比次数 = 元素个数 - 排序轮数 - 1

```cpp
#include<iostream>

using namespace std;

int main(){

    //冒泡排序

    int arr[9] = {4,2,8,0,5,7,1,3,9};

    //排序前
    cout << "排序前" << endl;
    for(int i=0;i<9;i++){
        cout<< arr[i];
    }
    cout << endl;

    for(int i =0;i<9-1;i++){ // 外侧的轮数，总共的轮数 = 元素-1
        for (int j =0; j<9-1-i;j++){ // 内层循环对比
            //如果第一个数字，比第二个数字大，交换两个数字

            if(arr[j]>arr[j+1]){

                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;             
            }
        }
    }

    //排序后结果
    cout << "排序后" << endl;
    for(int i =0; i < 9;i++){
        cout<< arr[i];
    }
    cout << endl;
}
```
