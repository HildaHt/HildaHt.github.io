---
title: 文章中的头文件配置
date:  2018-09-09 16:34:18 +0800
category: Minimalism
tags: deploy
excerpt: 打开或关闭单篇文章的一些配置选项。
---

创建一个名为 YYYY-MM-DD-NAME-OF-POST.md 的新文件，将 YYYY-MM-DD 替换为帖子的日期，并将 NAME-OF-POST 替换为帖子的名称。

以下是一篇文章的头信息配置示例：

```
---
title: "示例文章标题"
date: 2018-08-08 08:08:08 +0800
category: 分类
tags: 标签
comment: 是否开启评论
reward: 是否开启打赏
excerpt: 这是这篇文章的摘要。
---

正文内容
```

在文章列表页，就会显示每篇文章的摘要。摘要的截取，有两种方式，一个是在 YAML 头信息中直接写出，如上 (2018-08-08-example.md) 示例，另一种是从正文内容中截取，即使用'<!--more-->'标签。