# 常用集合算法

**算法简介：**

* `set_intersection` // 求两个容器的交集
* `set_union` // 求两个容器的并集
* `set_difference` // 求两个容器的差集

## 1. set\_intersection

**功能描述：**

* 求两个容器的交集

**函数原型：**

*   `set_intersection(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);`

    // 求两个集合的交集

    // **注意:两个集合必须是有序序列**

    // beg1 容器1开始迭代器 // end1 容器1结束迭代器 // beg2 容器2开始迭代器 // end2 容器2结束迭代器 // dest 目标容器开始迭代器

