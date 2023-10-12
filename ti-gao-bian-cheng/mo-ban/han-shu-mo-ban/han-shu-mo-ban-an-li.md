# 函数模板案例

案例描述：

* 利用函数模板封装一个排序的函数，可以对**不同数据类型数组**进行排序
* 排序规则从大到小，排序算法为**选择排序**
* 分别利用**char数组**和**int数组**进行测试

```cpp
#include<iostream>
using namespace std;

//实现通用 对数组进行排序的函数

//交换的函数模板
template<typename T>
void mySwap(T &a, T&b)
{
	T temp = a;
	a = b;
	b = temp;
}

//排序算法
template<typename T>
void mySort(T arr[],int len){
    for(int i =0;i < len;i++){
        int max = i; //认定最大值的下标
        for(int j = i+1;j < len;j++){
            //我们认定的最大值 比遍历出的数值要小， 说明j下标的元素菜市真正的最大值
            if(arr[max] < arr[j]){
                max =j; //更新最大值下标
            }
        }
        if(max!=i){
            //交换max和i下标的元素
            mySwap(arr[max],arr[i]);
        }
    }
}

//打印数组模板

template<class T>
void printArray(T arr[],int len){
    for(int i =0;i<len;i++){
        cout << arr[i] << " ";
    }
    cout << endl;
}

void test01(){
    //测试char数组

    char charArr[] = "badcfe";
    int num = sizeof(charArr) / sizeof(charArr[0]);
    mySort(charArr,num);
    printArray(charArr,num);

}

void test02(){
    int intArr[] = {7, 5, 8, 1, 3, 9, 2, 4, 6};
    int num = sizeof(intArr) / sizeof(int);
    mySort(intArr,num);
    printArray(intArr,num);
}
int main(){
    // test01();
    test02();

}
```
