---
title: "封面（Cover）"
date: 2023-10-22T07:43:49+08:00
description: |
    定制站点的封面页，如：首页、关于页。
weight: 50
---

这些页面通常作为独特的封面页：

+ `content/_index.md` —— 首页
+ `content/about.md` —— 关于页

根据[模板优先级](https://gohugo.io/templates/lookup-order/)，封面页最终使用 [layouts/_default/baseof.html](https://github.com/google/docsy/blob/main/layouts/_default/baseof.html) 作为页面模板。这个模板只有 header 和 footer。

## 背景图 background

Docsy 提供 [layouts/shortcodes/blocks/cover.html](https://github.com/google/docsy/blob/5295589fd575084a17774a0e93a12f5708e9b7c4/layouts/shortcodes/blocks/cover.html#L3) 简码来生成封面页背景图。

1. 添加图片 "content/featured-background.jpg" (图片包含`background`即可)
1. 调用简码

    ```html
    {{%/* blocks/cover title="Welcome to Docsy!" image_anchor="top" height="full" */%}}
    <a class="btn btn-lg btn-primary me-3 mb-4" href="{{%/* relref '/about' */%}}">
    Learn More <i class="fa-solid fa-circle-right ms-2"></i>
    </a>
    <a class="btn btn-lg btn-secondary me-3 mb-4" href="https://github.com/google/docsy">
    Download <i class="fa-brands fa-github ms-2 "></i>
    </a>

    A Hugo theme for creating great technical documentation sites
    {.lead .mt-5}

    {{%/* blocks/link-down color="info" */%}}
    {{%/* /blocks/cover */%}}
    ```

    参数：

    + `title`
    + `subtitle`
    + `byline`
    + `color`
    + `height`
    + `image_anchor`
    + `logo_anchor`
