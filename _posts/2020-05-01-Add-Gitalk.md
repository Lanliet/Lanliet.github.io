---
layout: post
title: 許久不見的流水賬
categories: [blog ]
tags: [折騰 ]
description:
---

# 給我的 Jekyll 博客添加 Gitalk

今天終於想辦法在博客裏添加了評論區，熱淚盈眶。

我選擇的是 [gitalk](https://github.com/gitalk/gitalk)。

首先在 Github 頁面右上角選擇 `Settings`，然後進入 `Developer settings` – `OAuth Apps` – `New OAuth App`。在裏面填寫 `Application name`（任意）、`Homepage URL`、`Authrization callback URL`（博客網頁，我這裏是 `http://lanliet.me`）。提交之後獲得 `Client ID` 和 `Client Secret`。

接下來在 `_layouts/posts.html` 裏，正文以下的位置添加如下代碼：

```<!-- Gitalk start -->
<div id="gitalk-container"></div> <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
<script>
  var title = location.pathname.substr(0, 50);
  var gitalk  = new Gitalk ({
      clientID: '獲得的 Client ID',
      clientSecret: '獲得的 Client Secret',
      repo: 'Lanliet.github.io',
      owner: 'Lanliet',
      admin: ['Lanliet'],
      id: title
      distractionFreeMode: false  // Facebook-like distraction free mode
      })
      gitalk.render('gitalk-container')
</script>
<!-- Gitalk end -->
```

然後對評論系統初始化，這樣就大功告成了！