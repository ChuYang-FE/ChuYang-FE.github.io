---
title: Mac必备神器——Homebrew
date: 2021-04-06 21:28:50
category: 
- [技术]
tags: [技术, Mac, 效率]
---

你是否曾经：想安装某个软件，却发现 App Store 没有上架该软件（例如VS Code）🤬，然后需要进行：打开搜索引擎搜索进入官网、下载、安装、删除安装包……一系列烦人操作？如果是，看万这篇文章，相信你会直呼“**相见恨晚🥺**”

<!-- more -->

## 背景

在 {% post_link 02_MacBook前端开发必备清单 %} 中，本羊简要介绍了下 HomeBrew ，如果你没看过那篇文章，这里本羊再当一遍复读机：

> [Homebrew](https://brew.sh/index_zh-cn) 是一款用于 macOS 的开源的软件包管理器，能够帮助你快速下载软件。

   **那为什么要选Homebrew？**

   一般情况下，在 Mac 上安装软件程序，通常是在 Mac App Store 搜索，然后安装。但是，对于不在 Mac App Store 上架的软件，你需要：

   1. 先在搜索引擎中搜索，找到官网，

   2. 然后打开下载页面下载，

   3. 最后再将下载的安装包拖到「软件程序」文件夹或执行安装。

   4. 清理安装包

   这也太麻烦了吧😅😅😅

   而使用Homebrew，你只需要在终端输入一行命令，就可以解决包括查找、下载和安装软件的一系列步骤。

   例如安装Chrome浏览器，你只需在终端输入：

   `brew install google-chrome`

   例如安装git：

   `brew install git`

   是不是非常简单快捷？👏👏👏 不多啰嗦，直奔主题吧！

## 安装及用法

### 安装 Homebrew

在终端输入：

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

### 安装软件

在以前，安装软件需要特意注明 `install cask` ，现在可以直接 `install` 想要安装的软件即可：

`brew install 软件名`

以安装强大的 IINA 播放器为例子，如下图：

![安装 IINA](/images/brew-install.jpg)

tips: 安装的软件位于 usr/local/Caskroom 目录下。

### 卸载软件

`brew uninstall iina`

![卸载 IINA](/images/brew-uninstall.jpg)

### 显示所有的已安装的软件

`brew list`

### 升级homebrew （从github下载最新版本）

`brew update`

更多 brew 命令及可安装的软件可查看 [Homebrew](https://brew.sh/index_zh-cn) 官网。

## 总结

安装 Homebrew 以后，大幅提高了软件管理效率，告别了

>“要安装，请拖动此图标……”

再也不再需要像以前一样进行繁琐的操作了~🥳

## 彩蛋

当 App Store 的微信版本还停留在2.6时，谁又想到在 Homebrew 上微信已经更新了3.0版本呢？😎

`brew install wechat`

![微信 3.0](/images/wechat-tips.jpg)

既然是3.0版本，那就可以直接在电脑上刷朋友圈了！🤣

![微信 朋友圈](/images/wechat-moment.jpg)
