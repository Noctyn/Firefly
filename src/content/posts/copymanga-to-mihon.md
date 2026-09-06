---
title: copy2mihon：批量把拷贝漫画书架和阅读历史导入 Mihon
published: 2026-08-26
pinned: false
description: 把拷贝漫画的书架收藏和阅读历史直接转换成 Mihon / Tachiyomi 能识别的 .tachibk 备份文件，收藏多的话还是挺省事的。
tags: [Mihon, Tachiyomi, 拷贝漫画, CopyManga, 漫画]
category: 实用工具
slug: copymanga-to-mihon
image: https://i0.hdslb.com/bfs/new_dyn/c3b98b654a4479928ee845a6cee262993691012253813604.jpg
---

## 背景

平时如果同时用 **拷贝漫画** 和 **Mihon**，应该都遇到过一个挺麻烦的问题。

比如我在拷贝漫画里收藏了上百本漫画，后来想换到 Mihon 上看，结果发现只能一本一本地搜索，再一个个添加到书架。

几十本还好，几百本的话就真的有点折腾了。

所以我自己做了个小工具，叫 **`copy2mihon`**。

它可以直接把拷贝漫画里的**书架收藏**和**阅读历史**批量转换成 Mihon / Tachiyomi 能识别的 `.tachibk` 备份文件。

简单来说，就是把拷贝漫画的漫画库直接“搬”到 Mihon，不用重新一部部搜索。

---

## 怎么用？

整个过程其实不复杂，主要就是三步。

### 1. 先拿到拷贝漫画的 Token

先登录拷贝漫画，然后打开自己的书架：

`https://www.mangacopy.com/web/person/shujia`

如果这个地址打不开，也可以试试其他镜像站，比如：

`https://www.copy4000.com/web/person/shujia`

进入书架后按 **F12** 打开开发者工具，切到 **Network（网络）**。

然后在筛选框里搜索：

`collect`

或者：

`comics`

接着刷新一下页面，找到类似 `comics?limit=...` 的请求。

![](https://i0.hdslb.com/bfs/new_dyn/78d4a9afc2a00962a783a78f23cdf31f3691012253813604.png)

点开请求，在右边找到：

**Headers → Request Headers**

里面可以看到一个叫 `authorization` 的请求头。

把后面的 Token 复制下来就行，比如：

`Token cd7e7ffa36cf...`

![](https://i0.hdslb.com/bfs/new_dyn/267d0bcb477006955db96b68d34d29c53691012253813604.png)

这个 Token 相当于你的登录凭证，所以**不要发给别人，也不要贴到公开的地方**。

### 2. 下载 copy2mihon

接下来去 GitHub 的 Releases 页面下载对应系统的版本：

<https://github.com/Noctyn/copy2mihon/releases>

Windows 用户直接下载对应的 exe 就可以。

把程序放到一个单独的文件夹里，然后在这个文件夹里打开终端，运行：

```powershell
.\copy2mihon-windows-amd64.exe
```

之后跟着命令行里的提示操作就行。

![](https://i0.hdslb.com/bfs/new_dyn/f0611a12b63ab6d2b6a6927dd125a7f33691012253813604.png)

最后程序会生成一个 `.tachibk` 备份文件。

### 3. 导入 Mihon

生成备份之后，把 `.tachibk` 文件传到手机上。

然后打开 **Mihon**，进入：

**设置 → 数据和存储 → 还原备份**

选择刚才生成的备份文件，等它恢复完成就行。

如果你用的是 **Komikku** 或其他兼容 Tachiyomi 备份格式的客户端，基本也是一样的操作。

---

## 能导入什么？

目前主要就是两个东西：

- **拷贝漫画书架收藏**
- **拷贝漫画阅读历史**

所以不只是把收藏搬过去，连之前看到哪里也可以一起带过去。

对于平时收藏量比较大的人来说，还是能省不少时间。

特别是那种收藏了几百本漫画，然后突然想换 Mihon 的情况，不然真要一本一本重新加。

---

## 最后

这个工具本身没什么复杂的东西，主要就是帮忙把重复操作省掉。

如果你也正好有“拷贝漫画收藏了一大堆，想搬到 Mihon，但是又懒得一个个搜索”的需求，可以试试看。

项目地址：

<https://github.com/Noctyn/copy2mihon>
