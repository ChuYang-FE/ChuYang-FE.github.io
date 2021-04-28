---
title: Markdown实用技巧
date: 2021-04-24 23:39:15
category: 
- [技术]
tags: [技术, 记录, 博客]
---

早有耳闻**Markdown**，然而我一直没什么机会真正的接触它。但自开始写博博客以来，我便和它形影不离，才感叹：相见恨晚！🤩

<!-- more -->

> Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档，然后转换成有效的 HTML 文档。

## 前言

在没开始写博客之前，我更习惯在云笔记上写些想法、心得或随想。相较博客而言，在自己的笔记里可以放飞自我，不用在意格式，也不用在意排版，感觉只要只要记下了最核心的“内容”，便足矣。😂

那既然要写博客，可不能写的这么放飞自我，否则读者的表情...👇

![这写的是啥](/images/stickers/WTF.jpeg)

于是，我“被迫”有了真正使用 Markdown 的机会。😎

## 用法

下面简要介绍下基本语法~

### 标题

一个#是一级标题，二个#是二级标题，以此类推。共支持六级标题。

注：#后要跟个空格再写文字哦🥺

### 字体

#### 加粗（本羊用的最多🤩）

文字左右分别用两个*号包起来

效果：**我加粗了**

#### 斜体

文字左右分别用一个*号包起来

效果：*我歪了*

#### 斜体加粗

文字左右分别用三个*号包起来

效果：***我又粗又斜***

#### 删除线

文字左右分别用两个~~号包起来

效果：~~懒惰（bushi）~~ 科技，是第一生产力！👏

### 引用

例如本文开头关于 Markdown 的描述，就是用的引用（不知道为啥我觉得这个很酷😎）

使用方法：`>` 接引用。>可以无限嵌套哦。效果如下：

> 为何我的眼里常含泪水，因为我对前端爱得深沉。——羊本羊

### 本文 Markdown 展示

### 分隔线（还没用到过🥲）

连续三个或以上的 - 或 *

---

效果：👆

### 图片（我的最爱！😍）

写博客当然得加上图片，理由如下：

1. 补充说明
2. 增加文章丰富性
3. 我想用表情包！🤩

`![alt属性文本](图片地址 '可选标题')`

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。效果：

![啥？](/images/stickers/what.png)

### 超链接（常用😘）

`[超链接名](超链接地址 "可选超链接title")`

> tips: hexo中需变量：`{% post_link 效率神器——Alfred %}`

效果：

{% post_link 效率神器——Alfred %}

### 列表

#### 无序列表

`- + *` 均可

如

```markdown
- 小明
- 小美
- 小羊
```

效果：

- 小明
- 小美
- 小羊

#### 有序列表

```markdown
1. 小明
2. 小美
3. 小羊
```

效果：

1. 小明
2. 小美
3. 小羊

#### 列表嵌套

在上一级与下一级间以3个空格作为开头即可，效果：

1. 小明
   1. 明之子
   2. 明之女
2. 小美
   1. 美之子
   2. 美之女
3. 小羊
   1. 羊之子
   2. 羊之女

### 表格

`使用 | 来分隔不同的单元格，使用 - 来分隔表头和其他行`，用法：

```markdown
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
```

设置表格的对齐方式：

1. -: 设置内容和标题栏居右对齐。
2. :- 设置内容和标题栏居左对齐。
3. :-: 设置内容和标题栏居中对齐。

以 {% post_link Oh-My-Zsh中Git的常用快捷键 %} 这篇文章用到的为例，如：

```markdown
快捷键|完整写法
|:-|:-|
g|git
gaa|git add .
gcmsg|git commit -m
gcb|git checkout -b
gst|git status
gf|git fetch
gl|git pull
gup|git pull --rebase
grb|git rebase
gsta|git stash save
gstp|git stash pop
gcp|git cherry-pick
mg|git merge
gp|git push
```

效果：

快捷键|完整写法
:-|:-|
g|git
gaa|git add .
gcmsg|git commit -m
gcb|git checkout -b
gst|git status
gf|git fetch
gl|git pull
gup|git pull --rebase
grb|git rebase
gsta|git stash save
gstp|git stash pop
gcp|git cherry-pick
mg|git merge
gp|git push

### 代码

#### 单行代码

```markdown
`单行代码`
```

#### 代码块（用的很多😘）

用法如图：

![代码块](/images/markdown-block.png)

> tips: ```后跟js代表当前是JavaScript的代码块，方便高亮。

效果：

```js
  function showDemo() {
    console.log('Demo');
  }
```

## 总结

总的来说，平常用的 Markdown 语法主要是以上介绍的这些，已经足够应付日常的写作~

如果以后有用到其他的语法，我会继续补充本文章滴~😎

对了，补充一个 VS Code 插件 `Markdown All in One`， 可以实时预览~

![Markdown All in One 插件实时预览](/images/markdown-profile.png)
