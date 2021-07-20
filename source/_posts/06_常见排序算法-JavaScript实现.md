---
title: 常见排序算法-JavaScript实现
date: 2021-04-10 21:20:04
category: 
- [技术]
tags: [技术, 算法, JavaScript]
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

## 冒泡排序

> 每次比较如果发现较小的元素在后面，就交换两个相邻的元素
>
> 每轮循环比较后，该轮最后一个值就是该轮最大的值（即大的沉底，小的浮起）

![冒泡排序](/images/algorithms/bubble.gif)

```js
function bubbleSort(array) {
  for (let i = 0; i < array.length - 1; i++) {
    for (let j = 0; j < array.length - i - 1; j++) { // 每轮都会排好一个
      if (array[j] > array[j + 1]) {
        [array[j], array[j + 1]] = [array[j + 1], array[j]];
      }
    }
  }
  return array;
}
```

## 选择排序

> 选择排序是冒泡排序的改进。
>
> 选择排序先并不急于调换位置，而是每轮看哪个数最小就记下该数所在的位置minIndex，等该轮扫描完毕，再让最小值和当前指定值对换，这样一来每一轮比较都只需要换一次位置。
>
> 缺点：不是稳定排序。

![选择排序](/images/algorithms/select.gif)

```js
function selectSort(array) {
  let minIndex;
  for (let i = 0; i < array.length - 1; i++) {
    minIndex = i; // 假设本轮的第一个值为最小值
    for (let j = i + 1; j < array.length; j++) { // 默认第一个已排好
      if (array[j] < array[minIndex]) {
        minIndex = j
      }
    }
    if (i !== minIndex) {  //如果该最小值和原最小值不同，则交换其值
      [array[i], array[minIndex]] = [array[minIndex], array[i]];
    }
  }
  return array;
}
```

## 插入排序

> 重点：部分有序。将无序部分和有序部分进行比较，然后插入对应位置。
>
> 首先要实现局部有序：直接把第一个元素看成有序。
>
> 数据规模越小、数据有序程度越高，越高效（移动少）

![插入排序](/images/algorithms/insert.gif)

代码实现：

```js
function insertSort(array) {
  let temp;
  for (let i = 1; i < array.length; i++) {
    temp = array[i]; // 每轮取出当前值，避免被覆盖。
    let j = i - 1;
    while (j >= 0  && array[j] > temp) {
        array[j + 1] = array[j];
        j--;
      }
    array[j + 1] = temp;
  }
  return array;
}
```

## 希尔排序

> 希尔排序是插入排序的改进。
>
> 当数据规模较大时或有序程度不高时，插入排序的元素移动次数较多，插入效率不高。为了解决这个问题，希尔排序出现了。
>
> 希尔排序把较大的数据集合分割成若干个小组（逻辑上分组），然后对每一个小组分别进行插入排序，此时，插入排序所作用的数据量比较小（每一个小组），插入的效率比较高。

**实现过程**：先让数组中任意间隔为 gap 的元素有序，刚开始 gap 的大小可以是 gap = n / 2，接着让 gap = n / 4，让 gap 一直缩小，当 gap = 1 时，也就是此时数组中任意间隔为1的元素有序，此时的数组就是有序的了。

![希尔排序](/images/algorithms/Shell.gif)

代码实现：

```js
function shellSort(array) {
  let len = array.length;
  let gap = Math.floor(len / 2);
  let temp;
  while (gap > 0) { //gap不断减小

    // 相当于一个有间隔的插入排序
    for (let i = gap; i < len; i += gap) {
      temp = array[i];
      let j = i;
      while (j >= gap && array[j - gap] > temp) {
        array[j] = array[j - gap];
        j -= gap;
      }
      array[j] = temp;
    }

    gap = Math.floor(gap / 2);
  }
  return array;
}
```

## 快速排序

> 快速排序的基本思想：通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列。

![快速排序](/images/algorithms/.gif)

代码实现：

简单版：

```js
function quickSort(arr = []) {
  // 当数组长度小于等于1时，直接返回数组
  if (arr.length <= 1) return arr;
  const left = [];
  const right = [];
  const pivot = arr[0];
  for (let i = 1; i < arr.length; i++) {
    // 比指定值大的，推进右数组，否则推进左数组
    arr[i] > pivot ? right.push(arr[i]) : left.push(arr[i]);
  };
  return [...quickSort(left), pivot, ...quickSort(right)];
}
```

标准版：

```js
function quickSort(arr = []) {

}
```
