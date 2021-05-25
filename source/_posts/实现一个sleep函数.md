---
title: 实现一个sleep函数
date: 2021-05-25 12:11:18
tags: [技术, JavaScript]
---

从ES5、ES6+的角度实现一个sleep函数。

<!-- more -->

## ES6+

主要方式包括：Promise（常用）、Async/Await（常用）、Generator（较少使用）。

### Promise

```js
const sleep = time => {
  return new Promise(resolve => setTimeout(resolve, time))
}

sleep(1000).then(res => {
  console.log('Promise');
})
```

### Async/Await

```js
const sleep = time => {
  return new Promise(resolve => setTimeout(resolve, time))
}

async function output() {
  console.log('Async/Await---Start');
  await sleep(1000);
  console.log('Async/Await---End');
}

output();
```

### Generator

```js
function * sleepGenerator(time) {
  yield new Promise(resolve => setTimeout(resolve, time))
}

sleepGenerator(1000).next().value.then(() => {
  console.log('Generator');
})
```

## ES5

ES5主要通过setTimeout回调函数的方式实现。

### 使用回调

```js
function sleep(callback, time) {
  if (typeof callback === 'function') {
    setTimeout(callback, time);
  }
}

function output() {
  console.log('回调');
}

sleep(output, 1000);
```
