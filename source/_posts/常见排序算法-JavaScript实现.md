---
title: 常见排序算法-JavaScript实现
date: 2021-04-10 21:20:04
category: 
- [技术]
tags: [技术, 手撕代码, JavaScript]
---

前几天偶尔看到了一些排序算法的动态图，觉得非常生动且有助于理解。而自己也有一段时间没接触过各种算法了，因此决定整理一下，将他们拾起来 📝

<!-- more -->

### 术语介绍

1. 稳定排序：如果 a 原本在 b 的前面，且 a == b，排序之后 a 仍然在 b 的前面，则为稳定排序。

2. 非稳定排序：如果 a 原本在 b 的前面，且 a == b，排序之后 a 可能不在 b 的前面，则为非稳定排序。

3. 原地排序：原地排序就是指在排序过程中不申请多余的存储空间，只利用原来存储待排数据的存储空间进行比较和交换的数据排序。

4. 非原地排序：需要利用额外的数组来辅助排序。

5. 时间复杂度：一个算法执行所消耗的时间。

6. 空间复杂度：运行完一个算法所需的内存大小。

![对比图](/images/algorithms/sort-table.jpg)

## 插入排序

> 重点：部分有序。将无序部分和有序部分进行比较，然后插入对应位置。
>
> 首先要实现局部有序：直接把第一个元素看成有序。

![插入排序](/images/algorithms/insert.gif)

代码实现：

```js
function insertSort(array) {
  let i, j, temp;
  for (i = 1; i < array.length; i++) {
    temp = array[i]; // 每轮取出当前值，避免被覆盖。
    j = i - 1;
    while ( j >= 0  && array[j] > temp) {
        array[j + 1] = array[j];
        j--;
      }
    array[j + 1] = temp;
  }
  return array;
}
```
