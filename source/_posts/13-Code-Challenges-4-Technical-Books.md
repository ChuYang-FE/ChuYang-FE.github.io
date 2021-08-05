---
title: 'Code-Challenges: 4-Technical-Books'
date: 2021-08-05 22:21:26
tags: [技术, JavaScript, 算法, JS Code Challenges]
---

领英课程： `JavaScript Code Challenges` 系列：EP4- [Technical Books](https://www.linkedin.com/learning/javascript-code-challenges/technical-books?u=2113185)

<!-- more -->

## 描述

> 题目只作简要描述，具体题目请点击上方👆🏻标题跳转。

继承 挑战1（{% post_link 12_Code-Challenges-1-Available-Books %}）中的 `Book` 类，并新增一个 `edition` 属性，使用 `getEdition()` 方法获取当前版本。

```js
// 挑战1中的 Book 类
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

## 实现

```js
class TechnicalBook extends Book {
  constructor(title, author, ISBN, numCopies, edition) {
    super(title, author, ISBN, numCopies);
    this.edition = edition;
  }

  getEdition() {
    return `The current version of this book is ${this.edition}.`;
  }
}

const myTechnicalBook = new TechnicalBook(
  '......', // 继承原属性
  '2.0', // edition
);

myTechnicalBook.getEdition();
```
