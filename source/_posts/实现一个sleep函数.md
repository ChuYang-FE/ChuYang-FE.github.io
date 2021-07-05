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
const sleep = time => new Promise(resolve => setTimeout(resolve, time))

// 1秒后，打印‘Promise’
sleep(1000).then(res => {
  console.log('Promise');
})
```

### Async/Await

```js
const sleep = time => new Promise(resolve => setTimeout(resolve, time))

async function output() {
  console.log('Async/Await---Start');
  await sleep(1000);
  console.log('Async/Await---End');
}

// 先直接打印 Async/Await---Start，1秒后打印 Async/Await---End
output(); 
```

### Generator

```js
function* sleepGenerator(time) {
  yield new Promise(resolve => setTimeout(resolve, time))
}

sleepGenerator(1000).next().value.then(() => {
  console.log('Generator');
})

// 1秒后，打印‘Generator’
```

## ES5

ES5主要通过setTimeout回调函数的方式实现。

### 使用回调

```js
function sleep(callback, time) {
  if (typeof callback === 'function') {
    setTimeout(callback, time);
  } else {
    console.log('回调函数错误');
  }
}

function output() {
  console.log('回调');
}

// 1秒后，打印‘回调’
sleep(output, 1000);
```
