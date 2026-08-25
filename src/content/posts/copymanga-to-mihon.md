---
title: copy2mihon：批量将拷贝漫画书架与阅读历史导入到 Mihon
published: 2026-08-26
pinned: false
description: 将拷贝漫画（CopyManga）的书架订阅和阅读历史导出为 Mihon / Tachiyomi 兼容的 .tachibk 备份文件。
tags: [Mihon, Tachiyomi, 拷贝漫画, CopyManga, 漫画]
category: 实用工具
slug: copymanga-to-mihon
image: https://i0.hdslb.com/bfs/new_dyn/c3b98b654a4479928ee845a6cee262993691012253813604.jpg
---

## 背景

对于漫画爱好者而言，**[Mihon](https://mihon.app/)** 是非常不错的开源漫画聚合阅读器，其中 **拷贝漫画** 则是目前资源最多的漫画源之一。但如果拷贝漫画收藏了上百本以上的漫画，想要手动一个个去 Mihon 搜索、添加书架还是非常的费时费力。

为了解决这个问题，我开发了一个脚本： **`copy2mihon`**。它可以批量将拷贝漫画的**全部书架收藏**与**阅读历史记录**直接转换或双向合并为 Mihon 官方标准备份格式（`.tachibk`）。

---

## 使用方法

### 一、获取拷贝漫画 Token

1. 登录并进入个人书架
   打开`https://www.mangacopy.com/web/person/shujia`，或`https://www.copy4000.com/web/person/shujia`等镜像站。
2. 找到 API 接口
   在书架页面按 F12，打开 Network（网络），在筛选框中输入 collect/comics，刷新页面，找到类似 comics?limit=... 的请求。
   ![](https://i0.hdslb.com/bfs/new_dyn/78d4a9afc2a00962a783a78f23cdf31f3691012253813604.png)
3. 复制 Token
   点击对应请求，在右侧打开 Headers（标头），找到 Request Headers（请求标头） 中的 authorization。复制后面的 Token，例如： `Token cd7e7ffa36cf...`
   ![](https://i0.hdslb.com/bfs/new_dyn/267d0bcb477006955db96b68d34d29c53691012253813604.png)

### 二、下载运行

在[`https://github.com/Noctyn/copy2mihon/releases`](https://github.com/Noctyn/copy2mihon/releases) 里下载自己系统对应的文件，移动到独立目录，然后右键打开终端，输入`.\copy2mihon-windows-amd64.exe`回车进行交互式向导运行。
![](https://i0.hdslb.com/bfs/new_dyn/f0611a12b63ab6d2b6a6927dd125a7f33691012253813604.png)

### 三、导入 Mihon 还原备份

无论使用哪种方式生成的 `.tachibk` 文件，恢复步骤都一样：

1. 将生成的 `.tachibk` 备份文件发送至手机（QQ/微信/网盘/数据线）；
2. 打开手机上的 **Mihon / Komikku / Tachiyomi**；
3. 进入 **「设置」→「数据和存储」→「还原备份」**；
4. 选取该文件，等待恢复完成。

---

## 项目地址

- [GitHub - Noctyn/copy2mihon](https://github.com/Noctyn/copy2mihon)
