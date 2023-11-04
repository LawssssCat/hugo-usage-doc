---
title: 内容管理（Content-Management）🔥
date: 2023-10-22T07:43:49+08:00
description: |
    记录如何编写 `content/<section_name>/**/<content_name>.md` 文件。
    （涉及东西多，篇幅长）
weight: 80
---

{{< block/youtube id="0GZxidrlaRM" title="Creating & Organizing Content | Hugo - Static Site Generator | Tutorial 6" >}}

content 的目录结构

```
└── content
    ├── _index.md          // [home]            <- https://example.com/ **
    ├── about.md           // [page]            <- https://example.com/about/
    ├── posts               
    |   ├── _index.md      // [section]         <- https://example.com/posts/ **         
    |   ├── firstpost.md   // [page]            <- https://example.com/posts/firstpost/
    |   ├── happy           
    |   |   ├── _index.md  // [section]         <- https://example.com/posts/happy/ **
    |   |   └── ness.md    // [page]            <- https://example.com/posts/happy/ness/
    |   └── secondpost.md  // [page]            <- https://example.com/posts/secondpost/
    └── quote   
        ├── _index.md      // [section]         <- https://example.com/quote/ **           
        ├── first.md       // [page]            <- https://example.com/quote/first/
        └── second.md      // [page]            <- https://example.com/quote/second/

// hugo默认生成的页面, 没有对应的markdown文章
分类列表页面               // [taxonomyTerm]    <- https://example.com/categories/  **
某个分类下的所有文章的列表  // [taxonomy]        <- https://example.com/categories/one-category  **
标签列表页面               // [taxonomyTerm]    <- https://example.com/tags/  **
某个标签下的所有文章的列表  // [taxonomy]        <- https://example.com/tags/one-tag  **
```

> 中括号`[]`中标注的是页面的kind属性, 他们整体上分为两类: single(单页面 - page) 和 list(列表页 - home, section, taxonomyTerm, taxonomy).
