---
title: 布局定制（Layout-custom）📦
date: 2023-10-22T07:43:49+08:00
description: |
    通过模板（Templates）技术，预先定义好的页面样式。
weight: 70
---

官方文档：

+ <https://gohugo.io/templates/> (模板使用)

## 模板引擎

布局使用： 参考"[布局使用]({{< ref "layout-usage" >}})"

Hugo 使用 Go 中 [html/template 库](https://pkg.go.dev/html/template) 作为模板引擎。
通过模板引擎，可以解析模板中的 `{{...}}` 标签。
标签 `{{...}}` 在 Go 中称为 "Action" (动作)。
动作包括两种类型：数据求值和控制结构。

+ 基础语法

    ```go-html-template
    //点
    {{ . }}
    代表传递给模板的数据，表示当前模板的上下文，可以是 Go 语言中的任何类型，比如字符串、数组、结构体等
    点的使用参考：https://www.regisphilibert.com/blog/2018/02/hugo-the-scope-the-context-and-the-dot/

    //注释
    {{/* comment */}}

    //空格
    {{- pipeline -}} // 清除 pipeline 前后的空格
    {{- pipeline }} // 清除 pipeline 前面的空格

    //变量赋值
    {{$变量名 := "值"}}

    //条件判断
    {{if pipeline}} T1 {{else}} T0 {{end}}
    如果不为空则输出T1，否则输出T0
    {{if pipeline}} T1 {{else if pipeline}} T0 {{end}}

    //循环语句
    {{range pipeline}} T1 {{end}}
    pipeline 的值必须是数组，切片，map，channel，设置 点. 为数组，切片遍历 map 的值，输出T1

    //with 重设点.的值
    {{with pipeline}} T1 {{else}} T0 {{end}}
    如果 pipeline 的值为空， 点. 的值不受影响,输出T1，否则 点. 的值设置成 pipeline 的值，输出T0
    ```

+ 定义子模板

    ```go-html-template
    //define
    {{define "name"}} T1 {{end}}
    定义一个特定名称的模板

    //template
    {{template "name"}}
    引入指定名称的模板，不传入任何数据.

    {{template "name" pipeline}}
    引入指定名称的模板，设置模板上下文 点. 的值为 pipeline 的值

    //block
    {{block "name" pipeline}} T1 {{end}}
    定义特定名称的模板，并在当前位置引入该名称的模板，模板的上下文 点. 的值为 pipline 的值，如果该名称的模板未实现(不存在)，则输出T1
    ```

## 变量/函数/数据

官方文档：

+ <https://gohugo.io/variables/> (变量列表)
+ <https://gohugo.io/functions/> (函数列表)

本站示例： {{% ref "test-template" %}}

视频教程：

{{% block/youtube id="ZyXlpKkgbFc" title="Variables | Hugo - Static Site Generator | Tutorial 17" %}}
{{% block/youtube id="w1NkCb3IJd0" title="Functions | Hugo - Static Site Generator | Tutorial 18" %}}
{{% block/youtube id="FyPgSuwIMWQ" title="Data Files | Hugo - Static Site Generator | Tutorial 20" %}}

## 逻辑

视频教程：

{{% block/youtube id="juSnHsCX9RU" title="If Statements | Hugo - Static Site Generator | Tutorial 19" %}}
