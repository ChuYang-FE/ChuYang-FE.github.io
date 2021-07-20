---
title: 效率神器——Alfred
date: 2021-04-17 23:59:52
category: 
- [技术]
tags: [技术, 效率, 工具]
---

> 如Alfred官方所述：Alfred是一款屡获殊荣的macOS应用程序，可通过热键，关键字，文本扩展等功能提高您的效率。搜索Mac和网页的内容，并通过自定义操作来控制Mac来提高生产力。😍

<!-- more -->

## 前言

Alfred与Mac自带的“聚焦”有何区别呢？简单来说，Alfred就是一个更强大的“聚焦”。

本文将介绍本羊自己用的比较多的功能，如粘贴板、终端、搜索文件、搜索文件内部内容等。

直接按下 `⌥ + 空格` 唤出 Alfred，基本操作就不多介绍了，直接开始！！

## 常用功能

1. 剪贴板（强烈推荐！！🤩）

   电脑换成MacBook以后，我发现macOS上竟然没有那个极其方便的功能 —— **剪切板😱**！！

   在Windows系统上，可以一次性复制多个项，然后只需按下 `Win + V` 唤出剪切板，即可方便快捷地进行批量粘贴操作。

   而macOS没有该功能！！😩 作为一名 ~~Ctrl CV工程师~~ 需要经常用到该功能的程序员，当然不可接受。而Alfred，让你不用额外安装剪切板软件，即可实现该功能。🤩

   使用方法：`⌥ + ⌘ + C`

   ![剪切板](/images/alfred/clipboard.png)

   支持文本、图片~

2. 搜索

   1. 浏览器搜索（支持检索浏览器历史记录、书签、搜索引擎）

      ![浏览器搜索](/images/alfred/browser-search.png)

   2. 本地搜索（文件搜索、文件内部内容搜索）

      文件搜索： `'`（或者在设置里直接设置成空格），接内容即可检索文件。

      ![文件搜索](/images/alfred/file-search.png)

      文件内部内容搜索： `in` 接内容即可检索文件。例如，我这篇文章的摘要包含了“**屡获殊荣**”四个字，因此本文件也被检索到了🤩

      ![文件内容搜索](/images/alfred/in-search.png)

   3. 其他自定义搜索（如在指定网站搜索，例如YouTube、MDN、StackOverflow）

      ![油管搜索李子柒🤩](/images/alfred/YouTube-search.png)

3. 自定义文本片（Snippet）

   需要经常输入指定内容？太长不想手打？**自定义文本片** 了解一下😎。

   ![用法非常简单](/images/alfred/snp-setting.png)

   用法：`snip 关键词` ，输入关键字后，会自动弹出自定义内容。日常用法：每次写东西前习惯标个今天日期，可以自定义 `{date}` 即可代表今天。使用时，只需 `snip today` 然后回车，自动生成2021-04-22🤩

   ![身份证太长不想输咋办](/images/alfred/snp-id.png)

4. 直接输入终端命令

   不想每次打开终端再输入命令执行咋办？直接 `>命令` 了解一下🤩

   ![直接执行命令](/images/alfred/alfred-terminal.png)

   ![效果](/images/alfred/terminal-date.png)

   注意，Alfred默认使用默认终端，若想使用 `iterm` ，可以在Alfred里选Terminal-“自定义”，配置如下：

   ``` AppleScript
      on alfred_script(q)
        if application "iTerm2" is running or application "iTerm" is running then
          run script "
            on run {q}
              tell application \"iTerm\"
                activate
                try
                  select first window
                  set onlywindow to true
                on error
                  create window with default profile
                  select first window
                  set onlywindow to true
                end try
                tell the first window
                  if onlywindow is false then
                    create tab with default profile
                  end if
                  tell current session to write text q
                end tell
              end tell
            end run
          " with parameters {q}
        else
          run script "
            on run {q}
              tell application \"iTerm\"
                activate
                try
                  select first window
                on error
                  create window with default profile
                  select first window
                end try
                tell the first window
                  tell current session to write text q
                end tell
              end tell
            end run
          " with parameters {q}
        end if
      end alfred_script
   ```

## 总结

更多其他常用功能及强大的Workflow日后继续补充，更多使用方法可参考 [Alfred官方](https://www.alfredapp.com/)~😎
