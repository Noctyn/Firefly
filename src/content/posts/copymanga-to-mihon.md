---
title: copy2mihon：把拷贝漫画的书架和阅读记录直接搬到 Mihon
published: 2026-08-26
pinned: false
description: 一个小工具，把拷贝漫画的书架和阅读历史导出成 Mihon / Tachiyomi 可以直接还原的 .tachibk 备份。
tags: [Mihon, Tachiyomi, 拷贝漫画, CopyManga, 漫画]
category: 实用工具
slug: copymanga-to-mihon
image: https://i0.hdslb.com/bfs/new_dyn/c3b98b654a4479928ee845a6cee262993691012253813604.jpg
---

## 背景

最近在折腾 Mihon 时遇到个问题。

就是我的拷贝漫画里订阅了不少漫画，想换到 Mihon 上看，但总不能再把书架里的漫画一部一部搜出来，然后重新加一遍，这样太繁琐、太累了。

尤其是收藏比较多的时候，上百本甚至上千本，想一个个加这个过程还是挺麻烦的。

于是就顺手做了个Python脚本 `copy2mihon`，主要作用就是：将拷贝漫画的**书架收藏**和**阅读历史**导出来，转换成 Mihon / Tachiyomi 可以识别的 `.tachibk` 备份文件。

这样可以直接用 Mihon 还原备份功能就行了，不用重新加几百本漫画。

## 使用方法

### 一、先拿到拷贝漫画 Token

先登录拷贝漫画，进入自己的书架：

`https://www.mangacopy.com/web/person/shujia`

如果这个地址打不开，也可以试试其他镜像站，比如：

`https://www.copy4000.com/web/person/shujia`

进入书架后按 F12，打开开发者工具，切到 **Network（网络）**。

然后在筛选框里搜 `collect/comics`，刷新一下页面。

找到类似 `comics?limit=...` 的请求。

![](https://i0.hdslb.com/bfs/new_dyn/78d4a9afc2a00962a783a78f23cdf31f3691012253813604.png)

点进去以后，在右边找到：

**Headers → Request Headers**

里面会有一个 `authorization`，复制后面的 Token 就可以了。

大概长这样：

`Token cd7e7ffa36cf...`

![](https://i0.hdslb.com/bfs/new_dyn/267d0bcb477006955db96b68d34d29c53691012253813604.png)

在这里要提醒一下，这个 Token 相当于你的登录凭证，**不要贴出来，也别随便发给别人**。

### 二、下载运行

去 GitHub 的 Releases 页面下载对应系统的版本：

<https://github.com/Noctyn/copy2mihon/releases>

Windows 直接下载 exe 就行。

把文件放到一个单独的文件夹里，然后在这个文件夹打开终端，运行：

```powershell
.\copy2mihon-windows-amd64.exe
```

接下来按照提示操作就行。

![](https://i0.hdslb.com/bfs/new_dyn/f0611a12b63ab6d2b6a6927dd125a7f33691012253813604.png)

操作完成后，会得到一个 `.tachibk` 文件。

### 三、导入 Mihon

把生成的 `.tachibk` 文件传到手机上。

然后打开 Mihon，进入：

**设置 → 数据和存储 → 还原备份**

选择刚才生成的备份文件，等它跑完就可以了。

如果你用的是 Komikku、Tachiyomi 之类支持这个备份格式的客户端，基本也是一样的。

## 可以导出什么内容？

目前就是这两部分：

- 书架里的收藏
- 阅读历史

所以不只是把漫画重新加到书架，之前的阅读记录也可以一起带过去。

对我这种收藏比较多的人来说，最大的好处就是省掉了一堆重复操作。

## 最后

其实就是个挺小的工具，没什么特别复杂的功能。

不过如果你正好准备从拷贝漫画换到 Mihon，又不想把书架里的漫画重新搜一遍，还是挺方便的。

项目地址：

<https://github.com/Noctyn/copy2mihon>
