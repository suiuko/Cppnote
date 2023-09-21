# 函数的常见样式

```cpp
// 函数常见样式
// 1. 无参无返
 
void test01(){
  cout << "this is test01" << endl;
 }

//2.有参无返
 void test02(){
  cout << "this is test02" << a << endl;
 }
 
 //3. 无参有返
 int test03(){
  cout << "this is test03" << endl;
  return 1000;
 }
 
 //4. 有参有返
 
 int test04(){
   cout << "this is test04 a = " << a << endl;
   return a;
 }

int main(){
  // 无参无返 函数调用
  test01();
  
  //有参无返 函数调用
  test02();
  
  // 无参有返 
  int num1 = test03();
  cout << "num1 =" << num1 << endl;
  
  //有参有返
  int num2 = test04(1000);
  cout << "num2 = " << num2 << endl;
}
 
```
