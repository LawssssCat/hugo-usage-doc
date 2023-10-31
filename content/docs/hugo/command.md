---
title: 命令行（Command）
# linkTitle: cli
date: 2023-10-22T07:43:49+08:00
description: |
    记录 Hugo 常用命令行
weight: 20
---

命令行顾名思义，这里不赘述其具体用法 (具体用法参考`hugo -h`或[官方文档](https://gohugo.io/commands/))；这里仅做分类，作用快速查找。

帮助

```bash
hugo compeletion [bash/fish/powershell/zsh]
hugo gen [doc/man]
```

环境

```bash
hugo version
hugo env
hugo config 
hugo config mounts
hugo list [all/drafts/expired/future]
```

构建 🔥

```bash
hugo new site <project_name>
hugo new theme <theme_name>
hugo new <page_name>
```

测试 🔥

```bash
hugo serve --buildDrafts --buildExpired --buildFuture 
```

模块

```bash
hugo mod [graph]
hugo mod init 
...
```

转换/迁移

```bash
hugo import [jekyll]
hugo convert [toJSON/toTOML/toYAML] # 不建议使用
```

发布 🔥

```bash
hugo --cleanDestinationDir --minify
hugo deploy
```
