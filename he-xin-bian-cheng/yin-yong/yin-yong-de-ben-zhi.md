# 引用的本质

本质：**引用的本质在c++内部实现是一个指针常量.**

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

初始化引用的时候，自动转换为 int \* const ref = \&a; 指针常量的指向不能修改了，但是 解引用中的数据是可以修改的。具体看上边的图。
