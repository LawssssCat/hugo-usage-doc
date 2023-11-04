---
title: 目录结构（Directory-structure）🔥
date: 2023-10-22T07:43:49+08:00
description: |
    记录 Hugo 如何划分目录功能。
weight: 30
---

官方文档： <https://gohugo.io/getting-started/directory-structure/>

{{< block/youtube id="sB0HLHjgQ7E" title="Creating a New Site / Directory Structure | Hugo - Static Site Generator | Tutorial 4" >}}

项目目录结构：

```
example/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── static/
├── themes/
└── config.toml
```

## config.toml —— 存放配置

官方文档：

+ <https://gohugo.io/getting-started/configuration/#all-configuration-settings> (可用配置)

配置可以统一记录在一个文件中：

{{< tabpane >}}
{{< tab header="Configuration file:" disabled=true />}}
{{< tab header="config.toml" lang="toml" >}}
contentDir = "content/en"
defaultContentLanguage = "en"
defaultContentLanguageInSubdir = false
[[menu.main]]
    name = "GitHub"
    weight = 50
    url = "https://github.com/google/docsy/"
    pre = "<i class="fa-brands fa-github"></i>"
    post = "<span class='alert'>New!</span>"
[languages]
[languages.en]
title = "Docsy"
description = "Docsy does docs"
languageName ="English"
# Weight used for sorting.
weight = 1
[languages.no]
title = "Docsy"
description = "Docsy er operativsystem for skyen"
languageName ="Norsk"
contentDir = "content/no"
time_format_default = "02.01.2006"
time_format_blog = "02.01.2006"
{{< /tab >}}
{{< tab header="config.yaml" lang="yaml" >}}
contentDir: content/en
defaultContentLanguage: en
defaultContentLanguageInSubdir: false
menu:
  main:
    - name: GitHub
      weight: 50
      url: 'https://github.com/google/docsy/'
      pre: <i class="fa-brands fa-github"></i>
      post: <span class='alert'>New!</span>
languages:
  en:
    title: Docsy
    description: Docsy does docs
    languageName: English
    weight: 1 # used for sorting
  'no':
    title: Docsy
    description: Docsy er operativsystem for skyen
    languageName: Norsk
    contentDir: content/no
    time_format_default: 02.01.2006
    time_format_blog: 02.01.2006
{{< /tab >}}
{{< tab header="config.json" lang="json" >}}
{
  "contentDir": "content/en",
  "defaultContentLanguage": "en",
  "defaultContentLanguageInSubdir": false,
    "menu": {
    "main": [
      {
        "name": "GitHub",
        "weight": 50,
        "url": "https://github.com/google/docsy/",
        "pre": "<i class="fa-brands fa-github"></i>",
        "post": "<span class='alert'>New!</span>"
      }
    ]
  },
  "languages": {
    "en": {
      "title": "Docsy",
      "description": "Docsy does docs",
      "languageName": "English",
      "weight": 1
    },
    "no": {
      "title": "Docsy",
      "description": "Docsy er operativsystem for skyen",
      "languageName": "Norsk",
      "contentDir": "content/no",
      "time_format_default": "02.01.2006",
      "time_format_blog": "02.01.2006"
    }
  }
}
{{< /tab >}}
{{< /tabpane >}}

> 新版配置文件名使用 `hugo.yaml`/`hugo.toml`/`hugo.json`。当然，向上兼容。

为了便于管理，也可以将其拆分为多个文件。
另一个好处是可以配置多个场景（profile）以应对不同情况的配置需求，比如`production`是发布时使用的配置，`staging`是本地预览时使用的配置。

```bash
├── config
│   ├── _default
│   │   ├── config.toml
│   │   ├── languages.toml
│   │   ├── menus.en.toml
│   │   ├── menus.zh.toml
│   │   └── params.toml
│   ├── production
│   │   ├── config.toml
│   │   └── params.toml
│   └── staging
│       ├── config.toml
│       └── params.toml
```

## archetypes —— 文章原型

通过 `hugo new <文件名>.md` 命令生成的 `.md` 文章会自动填充 `archetypes/default.md` 模板定义的内容。

## assets —— 待加工资源

这里的文件可以被 Hugo Pipes 调用并处理，然后发布到 `public/` 目录。

官方文档：

+ "Hugo Pipes" <https://gohugo.io/hugo-pipes/>

## static —— 静态资源

存放静态文件，比如图片、CSS、JS

> 区别 `assets/` 和 `static/` 目录：
>
> + `assets/` —— 经过 Hugo Pipes 加工后才移动
> + `static/` —— 原封不动的移动到 `public/` 目录
>

## layouts —— 页面布局

转跳： [页面布局]({{< ref "layout" >}})

## themes —— 主题

一般将主题放进去后就不用管了。

> Tips： 遇到问题可以直接看主题下的源码，有时比翻文档直接、快捷。前提需要对 Hugo 机制熟悉。

```
├── layouts
└── themes
    └── mytheme
        └── layouts
            ├── 404.html             // 404页面模板
            ├── _default
            │   ├── baseof.html      // 默认的基础模板页, 使用的方式是'拼接', 而不是'继承'.
            │   ├── list.html        // 列表模板  
            │   └── single.html      // 单页模板
            ├── index.html           // 首页模板
            └── partials             // 局部模板, 通过partial引入
                ├── footer.html
                ├── header.html
                └── head.html      
```

## content —— 内容管理

转跳： [内容管理]({{< ref "content-management" >}})

## data —— 站点数据

官方文档：

+ "Data templates" <https://gohugo.io/templates/data-templates/>

这里定义的数据可以在 `config.yaml` 中使用或者在 `layouts/` 中通过 `$.Site.Data` 获取。

e.g.

{{< tabpane >}}
{{< tab header="data/jazz/bass/jacopastorius" disabled=true />}}
{{< tab header=".toml" lang="toml" >}}
discography = ['1974 - Modern American Music … Period! The Criteria Sessions', '1974 - Jaco', '1976 - Jaco Pastorius', '1981 - Word of Mouth', '1981 - The Birthday Concert (released in 1995)', '1982 - Twins I & II (released in 1999)', '1983 - Invitation', '1986 - Broadway Blues (released in 1998)', '1986 - Honestly Solo Live (released in 1990)', '1986 - Live In Italy (released in 1991)', "1986 - Heavy'n Jazz (released in 1992)", '1991 - Live In New York City, Volumes 1-7.', '1999 - Rare Collection (compilation)', '2003 - Punk Jazz: The Jaco Pastorius Anthology (compilation)', '2007 - The Essential Jaco Pastorius (compilation)']
{{< /tab >}}
{{< tab header=".yaml" lang="yaml" >}}
discography:
- 1974 - Modern American Music … Period! The Criteria Sessions
- 1974 - Jaco
- 1976 - Jaco Pastorius
- 1981 - Word of Mouth
- 1981 - The Birthday Concert (released in 1995)
- 1982 - Twins I & II (released in 1999)
- 1983 - Invitation
- 1986 - Broadway Blues (released in 1998)
- 1986 - Honestly Solo Live (released in 1990)
- 1986 - Live In Italy (released in 1991)
- 1986 - Heavy'n Jazz (released in 1992)
- 1991 - Live In New York City, Volumes 1-7.
- 1999 - Rare Collection (compilation)
- '2003 - Punk Jazz: The Jaco Pastorius Anthology (compilation)'
- 2007 - The Essential Jaco Pastorius (compilation)
{{< /tab >}}
{{< tab header=".json" lang="json" >}}
{
   "discography": [
      "1974 - Modern American Music … Period! The Criteria Sessions",
      "1974 - Jaco",
      "1976 - Jaco Pastorius",
      "1981 - Word of Mouth",
      "1981 - The Birthday Concert (released in 1995)",
      "1982 - Twins I \u0026 II (released in 1999)",
      "1983 - Invitation",
      "1986 - Broadway Blues (released in 1998)",
      "1986 - Honestly Solo Live (released in 1990)",
      "1986 - Live In Italy (released in 1991)",
      "1986 - Heavy'n Jazz (released in 1992)",
      "1991 - Live In New York City, Volumes 1-7.",
      "1999 - Rare Collection (compilation)",
      "2003 - Punk Jazz: The Jaco Pastorius Anthology (compilation)",
      "2007 - The Essential Jaco Pastorius (compilation)"
   ]
}
{{< /tab >}}
{{< /tabpane >}}

`layouts/home.html`

```go-html-template
<ul>
  {{ range $.Site.Data.jazz.bass.jacopastorius.discography }}
  <li>{{ . }}</li>
  {{ end }}
</ul>
```

## public —— 发布目录

用于存放生成的站点文件

```bash
public/
├── categories/
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── post/
│   ├── my-first-post/
│   │   └── index.html
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── tags/
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── index.html
├── index.xml      <-- RSS feed for the site
└── sitemap.xml
```
