---
title: 终端体验提升计划-iTerm2 + Oh-My-Zsh
date: 2021-04-04 16:39:25
category: 
- [技术]
tags: [技术, 效率, Mac]
---

如何让你的终端用起来顺手又炫酷？看完本文，将让你的终端体验大幅提升😎

<!-- more -->

## 概述

在 {% post_link 02_MacBook前端开发必备清单 %} 中展示了MacBook前端开发的必备清单，本文将介绍其一： **iTerm2 + Oh-My-Zsh**

## 介绍

1. [iTerm2](https://iterm2.com/)

   > iTerm2是默认终端的替代品，也是目前Mac系统下最好用的终端工具，集颜值和效率于一身。

2. [Oh-My-Zsh](https://ohmyz.sh/)

   > Oh My Zsh 是一款社区驱动的命令行工具，正如它的主页上说的，Oh My Zsh 是一种生活方式。 它基于Zsh 命令行，提供了主题配置，插件机制，已经内置的便捷操作。它能让你用了直呼： **"Oh My ZSH!" 🤣👏** （它官网的确是这么说的哈哈哈哈）

## 安装

1. iTerm2

   安装：

   可以使用上一篇博客提到的Homebrew来安装：`brew install iterm2`

   也可以直接到 [iTerm2](https://iterm2.com/) 官网下载

2. Oh-My-Zsh

   安装：

   `sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

## 配置及使用

配置主题的前提：

   >1. 安装了 zsh
   >2. 安装了 powerline 字体
   >3. 安装方法参考：<https://github.com/powerline/fonts>

1. iTerm2

   先设置字体：

   进入偏好设置 -> Profiles -> Text -> Font -> 选择 `Meslo LG S for PowerLine`

2. Oh-My-Zsh

### 配置主题

   打开zsh配置：`vim ~/.zshrc`

   修改主题：`ZSH_THEME="agnoster"` 个人觉得agnoster主题最好看😍

   生效：`source ~/.zshrc`

   ![agnoster主题展示及自动补全插件](/images/theme-show.png)

### 配置插件

插件有自带的Git，让你可以使用简写，如：

`gaa` 就是 `git add --all`

更多常用git快捷键可以看 {% post_link 04_Oh-My-Zsh中Git的常用快捷键 %}

此外，还强烈建议装上以下的插件：

1. zsh-autosuggestion，命令建议和补全

    ``` zsh
    cd ~/.oh-my-zsh/custom/plugins/
    git clone https://github.com/zsh-users/zsh-autosuggestions
    ```

2. zsh-syntax-highlighting，代码高亮

   ``` zsh
   cd ~/.oh-my-zsh/custom/plugins/
   git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
   ```

3. z， 快速跳转到对应目录，让你不再疯狂输入cd

   只要你输入过该路径，以后你便可以直接使用 `z 该目录` 直接进入该目录，如下：

  ![z快速跳转](/images/z.jpg)

   由于 `z` 是 zsh 内置的，所以只需在 plugins中加入 z 即可

输入 `vim ~/.zshrc` 进入 .zshrc ，按 `i` 进入编辑状态，找到plugins，输入以下内容

``` zsh
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
  z
)
```

然后在文件的最后一行添加：

`source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh`

输入完成后，点击键盘`esc`键退出编辑模式，然后输入`:wq` 保存并退出，最后执行命令 `source ~/.zshrc` 使刚才的修改生效。

## 总结

经过以上步骤，你拥有了：

1. 非常好看的终端
2. 提高效率的插件：代码高亮、自动补全、快速路径跳转、Git命令快捷键

快去试试吧😎
