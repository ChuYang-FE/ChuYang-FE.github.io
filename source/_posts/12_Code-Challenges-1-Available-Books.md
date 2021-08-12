---
title: 'Code Challenges: 1-Available Books'
date: 2021-07-15 17:14:43
tags: [技术, JavaScript, 算法, JS Code Challenges]
---

领英课程： `JavaScript Code Challenges` 系列：EP1- [Available Books](https://www.linkedin.com/learning/javascript-code-challenges/available-books)

<!-- more -->

## 描述

> 题目只作简要描述，具体题目请点击上方👆🏻标题跳转。

### 参数

`title, author, ISBN, numCopies`

### 方法

`getAvailability()`：根据书本的库存返回对应提示

`sell(numSold)`：售出指定数量书本，若无传递参数，则为默认为1

`restock(numCopies)`：入库数量，若无传递参数，则为默认为5

### 清单

1. 使用类
2. 使用 getter 方法

## 代码实现

### Class

```js
class Book {
  constructor(title, author, ISBN, numCopies) {
    this.title = title;
    this.author = author;
    this.ISBN = ISBN;
    this.numCopies = numCopies;
  }

  get availability() {
    return this.getAvailability();
  }

  getAvailability() {
    if (this.numCopies <= 0) {
      return 'Out of stock';
    } else if (this.numCopies < 10) {
      return `Low stock: ${this.numCopies}`;
    }
    return `In stock: ${this.numCopies}`;
  }

  sell(numSold = 1) {
    if (this.numCopies <= 0) {
      console.log('No stock');
      return;
    }
    this.numCopies -= numSold;
  }

  restock(numCopiesStocked = 5) {
    this.numCopies += numCopiesStocked;
  }
}
```

### ES5

```js
function Book(title, author, ISBN, numCopies) {
  this.title = title;
  this.author = author;
  this.ISBN = ISBN;
  this.numCopies = numCopies;
}

Book.prototype.sell = function(numSold = 1) {
  ...
}

Book.prototype.restock = function(numCopiesStocked = 5) {
  ...
}

Book.prototype.getAvailability = function() {
  ...
}
```
