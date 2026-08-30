+++
authors = ["Gheyret"]
title = "Hugo 快速入门指南"
date = "2026-08-30"
description = "从零开始，用 Hugo 搭建一个静态博客的完整流程，涵盖安装、建站、写文章与部署。"
tags = [
    "hugo",
    "教程",
    "静态网站",
]
categories = [
    "技术笔记",
]
series = ["站点搭建"]
+++

Hugo 是目前最流行的静态站点生成器之一，以**构建速度极快**著称。这篇文章带你从零开始搭建一个博客。

<!--more-->

## 安装 Hugo

在 Windows 上推荐使用包管理器安装：

```powershell
# winget 安装（含 Sass 支持的 extended 版）
winget install Hugo.Hugo.Extended

# 或者用 chocolatey
choco install hugo-extended
```

安装完成后验证：

```powershell
hugo version
```

## 创建新站点

```powershell
hugo new site my-blog
cd my-blog
```

## 添加主题

```powershell
git init
git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
```

然后在 `hugo.toml` 中设置主题：

```toml
theme = "hugo-coder"
```

## 写第一篇文章

```powershell
hugo new posts/hello.md
```

生成的 Markdown 文件带有前置元数据（front matter）：

```markdown
+++
title = "Hello"
date = "2026-08-30"
draft = true
+++
```

## 本地预览

```powershell
hugo server -D
```

浏览器打开 `http://localhost:1313` 即可实时预览，保存文件后页面自动刷新。

## 部署

静态站点可以免费托管在 GitHub Pages / Cloudflare Pages / Netlify 上，只需构建 `hugo` 命令输出的 `public/` 目录。

Happy blogging! 🚀
