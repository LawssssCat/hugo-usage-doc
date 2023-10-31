---
title: 前置元数据（Frontmatter）
date: 2023-10-22T07:43:49+08:00
description: |
    设置文章的标题、创建日期、描述等。
weight: 10
---

官方文档：

+ <https://gohugo.io/content-management/front-matter/> (可用前置元数据列表)

{{< block/youtube id="Yh2xKRJGff4" title="Front Matter | Hugo - Static Site Generator | Tutorial 7" >}}

## 使用

page

```yaml
# content/test/_index.md
title: "My amazing new section"
weight: 1
type: docs
description: >
    A special section with a docs layout.
```

list/section

```yaml
# content/news/_index.md
title: "Latest News"
linkTitle: "News"
menu:
main:
    weight: 30
cascade:
    - type: "blog"
```

```yml
# content/sections01/_index.md 

# section 子文章"块"显示
simple_list: true # 列表显示
no_list: true # 不显示
```


链接 linking

+ `ref` —— 绝对路径
+ `relref` —— 相对路径

```bash go-html-template
# hostname=localhost
# port=1313
# baseurl=/
.
└── content
    ├── document1.md
    ├── about
    |   ├── _index.md
    |   └── document1.md
    ├── pages
    |   ├── current.md <----------- current
    |   ├── document1.md
    |   └── document2.md // has anchor #anchor
    ├── products
    |   └── index.md
    └── blog
        └── my-post.md

e.g. 
{{</* relref "document1.md" */>}} --> 可以忽略后缀
{{</* relref "document1" */>}} --> 输出： /content/pages/document/
{{</* ref "document1" */>}}    --> 输出： //localhost:1313/content/pages/document/
{{</* ref "document2.md#anchor" */>}}
{{</* ref "document1" */>}}        --> 找到： /content/pages/document1.md
{{</* ref "/document1" */>}}       --> 找到： /content/document1.md
{{</* ref "/about/document1" */>}} --> 找到： /content/aboug/document1.md
```

> 路径不需要绝对"准确"，hugo会(按照优先级)自动匹配最适合的结果。
>
> 优先级：
>
> 1. `./*`
> 1. `./**`
> 1. `content/*`
> 1. `content/**`
