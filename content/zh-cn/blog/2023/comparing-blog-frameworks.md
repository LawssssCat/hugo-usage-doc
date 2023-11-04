---
title: 博客构架工具对比
date: 2023-10-22T07:43:49+08:00
description: |
    对比博客构建工具的优缺点。
---

+ [x] dynamic | WordPress - PHP
    + 问题：
        + 环境。。。维护！维护！维护！
        + 插件。。。维护！维护！维护！
        + 安全警告？维护！维护！维护！
        + 性能。。。钱！钱！钱！
        + 备份！备份！备份！
+ [x] static | hugo - Go
    + [github](https://github.com/gohugoio/hugo) | 2023年10月23日 star=69k
    + themes
        + [academic](https://themes.gohugo.io/themes/starter-hugo-academic/) - 用途：个人博客
        + [docsy](https://github.com/google/docsy) - 用途：产品文档
        + [docuapi](https://github.com/bep/docuapi) - 用途：API文档
    + 问题：
        + 入门门槛相对高 (主要是概念多且相互关联。好在官方文档足够详细)
+ [x] static | jekyll - Ruby
    + [github](https://github.com/jekyll/jekyll) | 2023年10月23日 star=47k
    + 问题：
        + 环境复杂 (主要是不熟悉 Ruby 环境)
        + 中文资料不多
        + 构建时，插件需要同步更新
+ [x] static | hexo - node.js
    + [github](https://github.com/hexojs/hexo) | 2023年10月23日 star=37k
    + 问题：
        + 默认提供的功能相对有限
        + 插件需要定期更新维护
+ [ ] static | mkdocs - python
    + [github](https://github.com/mkdocs/mkdocs) | 2023年10月20日 star=17k
    + themes
        + [mkdocs-material](https://github.com/squidfunk/mkdocs-material) | 2023年10月20日 16k star
+ [ ] static | mdBook - Rust
+ [ ] ??? | Pelican - Python
+ [ ] ??? | Rails - ???
+ [ ] ??? | Express.js - node.js???
+ [ ] ??? | gitbook - ???
