+++
authors = ["Gheyret"]
title = "Coder 主题介绍与自定义"
date = "2026-08-30"
draft = true
description = "介绍本站使用的 Hugo Coder 主题，以及如何通过配置文件自定义导航菜单、头像和站点信息。"
tags = [
    "hugo",
    "coder",
    "主题",
    "自定义",
]
categories = [
    "技术笔记",
]
series = ["站点搭建"]
+++

[Coder](https://github.com/luizdepra/hugo-coder) 是一个极简风格的 Hugo 主题，界面清爽、加载快，非常适合个人博客。本站使用的就是它。

<!--more-->

## 主题特色

- 🎯 极简设计，专注内容
- 📱 完全响应式，移动端友好
- 🌙 支持暗色模式
- 🔍 内置搜索（可配置）
- 🌍 多语言支持
- 🚀 零 JavaScript 依赖，加载飞快

## 导航菜单配置

在 `hugo.toml` 中通过 `[[menu.main]]` 定义导航：

```toml
[[menu.main]]
  name = "首页"
  weight = 1
  url = "/"

[[menu.main]]
  name = "关于"
  weight = 2
  url = "/about/"

[[menu.main]]
  name = "项目"
  weight = 3
  url = "/projects/"
```

## 站点信息

```toml
[params]
  author = "Gheyret"
  description = "个人博客"
  avatarurl = "images/avatar.png"

  [params.social]
    github = "https://github.com/gheyret"
    email = "gheyret@example.com"
```

## 暗色模式

Coder 主题默认跟随系统切换明暗模式，也可以手动切换，无需额外配置。

## 结语

主题只是外壳，内容才是核心。希望这个博客能成为我持续输出的地方。
