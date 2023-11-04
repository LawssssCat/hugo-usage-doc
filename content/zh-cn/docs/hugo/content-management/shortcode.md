---
title: 简码（Shortcode）
date: 2023-10-22T07:43:49+08:00
description: |
    简码，顾名思义"用于简化操作的代码块"。
weight: 80
---

{{< block/youtube id="2xkNJL4gJ9E" title="Shortcodes | Hugo - Static Site Generator | Tutorial 9" >}}

{{< block/youtube id="Eu4zSaKOY4A" title="Shortcode Templates | Hugo - Static Site Generator | Tutorial 22" >}}

我们在文章内容 `content/**.md` 可以重复多处调用这种代码块来减少重复性操作。

> 区分： 简码（Shortcode）和模板变量与函数（Template variable and function）
>
> 模板的设计初衷是简化操作，避免重复编码。但是如果（表达作者思想的）文章中出现大量（页面渲染和逻辑判断相关的）模板语句会使文章管理变得混乱。
>
> 为了避免上述问题，Hugo 提出简码的概念： 文章作者不能直接在文章中使用模板语言，但是可以使用模板语言封装后的"简码（Shortcode）"。简码封装了模板语言涉及的html和逻辑判断。使用简码只需要传入必要参数即可。
>
> + 模板变量调用： `{{ .Title }}`
> + 模板函数调用： `{{ dict "title" .Title content" "hello!" | jsonify }}`
> + 简码调用： `{{</* highlight go */>}} hello {{</* /highlight */>}}`
>
> 总结： 模板只能在 `layouts/` 中使用；简码只能在 `content/` 中使用。这样就划分了两个角色： 编写模板的主题作者和编写文章的内容作者！

官方文档：

+ <https://gohugo.io/content-management/shortcodes/#use-hugos-built-in-shortcodes> (内置简码列表)
+ <https://gohugo.io/templates/shortcode-templates/> (自定义简码)
+ <https://gohugo.io/variables/shortcodes/> (自定义简码中可用变量)

### 调用

有两种调用形式：

+ `{{</* ... */>}}` —— 不对传入参数进行处理
+ `{{%/* ... */%}}` —— 对传入参数进行加工，如进行markdown标志的解析

有三种参数传递形式：

+ `{{</* shortcodename */>}}` —— 不传参
+ `{{</* shortcodename parameters */>}}` —— 传入 `"string"` 或者 `key="value"` 形式的参数 （简码中会通过 `.Get` 函数获取传入参数）
+ `{{</* shortcodename */>}} inner string {{</* /shortcodename */>}}` —— 用两个简码标记包裹字符串 （简码中会通过 `.Inner` 变量获取包裹的字符串）

### 简码"不解析"

有的时候，我们就希望简码字符直接以字符形式显示，像 "`{{</* string */>}}`" 这样。这时我们只需要将内容用 `/* ... */` 包裹，如 "`{{</*/* string */*/>}}`" 写在 `.md` 文件中。

```bash
{{</*/* string */*/>}} --解析--> {{</* string */>}} 
{{%/*/* string */*/%}} --解析--> {{%/* string */%}} 
```
