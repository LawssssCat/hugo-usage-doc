---
title: 标记解析（Markup）
date: 2023-10-22T07:43:49+08:00
description: |
    定义 Hugo 的 Markdown 解析器及其解析风格（包括：特殊字符解析规则、章节样式、代码高亮样式和表格样式）。 
weight: 40
---

官方文档： <https://gohugo.io/getting-started/configuration-markup/> (配置看这里)

所谓 "标记解析" 就是将 `.md` 文件中的各种特殊字符、特殊格式转换为 `.html` 文件形式。可以理解为渲染 `.md` 文件。

## Goldmark —— 解析 markdown 标记

Hugo 默认使用 [goldmark](https://github.com/yuin/goldmark/) 解析 markdown 标记。

下面记录常用配置

### unsafe

是否允许渲染 html 代码块。默认不渲染，替换为 `<!--raw HTML omitted -->` 代码块。

```yaml
# config/_default/markup.yml
goldmark:
  renderer:
    unsafe: true
```

### attribute

是否解析 `{...}` 额外语法。默认不解析，直接识别为普通文本。

```yaml
# config/_default/markup.yml
goldmark:
  parser:
    attribute:
      block: true
      title: true
```

```markdown
# title_01
{.myclass}

> foo
> bar
{.myclass}
```

### extensions

<https://github.com/yuin/goldmark/#extensions>

## Highlight —— 配置"代码高亮"风格

Hugo 使用 [chroma](https://github.com/alecthomas/chroma) 作为代码高亮解析器。

官方文档：

+ <https://gohugo.io/getting-started/configuration-markup/#highlight> (配置)
+ <https://gohugo.io/content-management/syntax-highlighting/> (简码形式)
+ <https://gohugo.io/functions/transform/highlight/> (函数形式)

```yaml {hl_lines=[4,"7-8"]}
# config/_default/markup.yml
highlight:
  anchorLineNos: false # 为每一行代码标注链接，如："#hl-3-6"为第三个代码块中第六行
  lineAnchors: "" # 链接前缀，默认"hl"
  codeFences: true # 解析{...}扩展选项
  guessSyntax: false # 猜测语法，关闭加速编译
  hl_Lines: ""
  hl_inline: false # 行高亮，一般不在这里设置，在codeFence中设置
  lineNoStart: 1
  lineNos: false # 行号
  lineNumbersInTable: true # 可能有适配问题，旧版本关闭的
  noClasses: true # 使用class标签，而不是内嵌的内联样式
  noHl: false
  style: monokai # 代码高亮主题，参考 https://xyproto.github.io/splash/docs/all.html
  tabWidth: 4
```

## Table of contents —— 右侧文章大纲配置

简称 "TOC"

```yaml
tableOfContents:
  ordered: false # 是否添加序号，默认false
  startLevel: 2 # 开始级别，默认1
  endLevel: 4 # 结束级别，默认3
```
