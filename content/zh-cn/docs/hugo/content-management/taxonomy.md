---
title: 分类法（Taxonomy）
date: 2023-10-22T07:43:49+08:00
description: |
    给文章打标签，便于检索。
weight: 90
---

{{< block/youtube id="pCPCQgqC8RA" title="Taxonomies | Hugo - Static Site Generator | Tutorial 10" >}}

默认有 `tags` 和 `categories` 两个。添加更多只需要在配置文件配置：

```yml
taxonomies:
  tag: tags
  category: categories
  project: projects
```

默认会把全部标签显示在右侧，称为 "标签云（taxonomyCloud）"。
可以配置只显示一部分标签：

```yaml
params:
  taxonomy:
    taxonomyCloud:
      - projects    # remove all entries
      - tags        # to hide taxonomy clouds
    taxonomyCloudTitle:   # if used, must have the same
      - Our Projects      # number of entries as taxonomyCloud
      - Tag Cloud
    taxonomyPageHeader:
      - tags        # remove all entries
      - categories  # to hide taxonomy clouds
```
