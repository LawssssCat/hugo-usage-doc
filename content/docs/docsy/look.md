---
title: 外观（Look）
date: 2023-10-22T07:43:49+08:00
description: |
    设置主题的样式、颜色、站点标识、站点图标等。
weight: 10
---

## 样式 style

+ `assets/scss/_variables_project.scss` 可以覆盖主题原有的变量值（在 `assets/scss/_variables.scss` 找到主题原有的变量值）和 [Bootstrap 变量默认值](https://getbootstrap.com/docs/4.1/getting-started/theming/#variable-defaults)。
+ `assets/scss/_styles_project.scss` 可以添加自己的自定义 SCSS 样式的地方，包括覆盖 Docsy 主题 SCSS 文件中的任何样式。

## 颜色 color

在 `assets/scss/_variables_project.scss` 中设置：

```scss
$primary: #390040;
$secondary: #A23B72;
```

## 站点标识 logo

将图片放在 `assets/icons/logo.svg` 会覆盖默认的站点标识。

通过配置 `navbar_logo: false` 也可以不显示站点标识。

## 站点图标 favicon

将图标放在 `static/favicons/` 中会覆盖默认的站点图标。

因为主题会在头文件中插入下面引用 `themes/docsy/layouts/partials/favicons.html`

{{< readfile file="/themes/docsy/layouts/partials/favicons.html" code="true" lang="go-html-template" >}}

> Tips： 通过 <http://cthedot.de/icongen>（允许您从单个图像创建各种图标大小和选项）或 <https://favicon.io> 可以快速创建一组网站图标。

## 图标样式 icon

<https://fontawesome.com/icons?d=gallery&m=free>
