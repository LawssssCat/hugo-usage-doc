---
title: 多语言支持（Multi-language）
date: 2023-10-22T07:43:49+08:00
description: |
    为页面框架、文章添加多国语言支持，也叫"国际化"。
---

官方文档：

+ <https://gohugo.io/content-management/multilingual/> (multilingual)

## 页面框架"国际化"

首先，需要在 `i18n/` 目录中定义多语言的显示内容。 （这些内容一般由主题项目提供）

```
i18n/
├── en.toml (默认)
└── zh-cn.toml <---- 新增
```

e.g. [docsy/i18n/zh-cn.toml](https://github.com/google/docsy/blob/main/i18n/zh-cn.toml)

```toml
[ui_pager_prev]
other = "上一页"

[ui_pager_next]
other = "下一页"

[ui_read_more]
other = "更多"
```

然后，在配置文件中更改 [defaultcontentlanguage](https://gohugo.io/getting-started/configuration/#defaultcontentlanguage) 配置设置。 （默认`en`）

```yaml
defaultcontentlanguage: zh-cn
```

最后，通过调用[模板函数](https://gohugo.io/functions/lang/translate/) `{{ T "ui_pager_prev" }}` 就能得到当前环境的框架文本。

## 文章内容"国际化"

<https://www.docsy.dev/docs/language/> \
<https://before80.github.io/docsy_docs_with_hugo/docs/Multi-languageSupport/>

```bash
content/en/
```

## 站点检索"国际化"

设置 [languagecode](https://gohugo.io/getting-started/configuration/#languagecode) 配置有利于浏览器和搜索引擎识别站点语言。

它的作用：

1. 改变内部 RSS 模板中的 `<language>` 元素
1. 改变内部别名模板中 `<html>` 元素的 lang 属性

取值参考： [HTML Language Code Reference](https://www.w3schools.com/tags/ref_language_codes.asp)
