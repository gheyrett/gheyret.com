+++
authors = ["Gheyret"]
title = "Markdown 语法速查手册"
date = "2026-08-30"
description = "一篇覆盖常用 Markdown 语法的速查文章，包含标题、列表、表格、代码块、引用、图片等。"
tags = [
    "markdown",
    "语法",
    "速查",
]
categories = [
    "技术笔记",
]
series = ["写作技巧"]
+++

写博客离不开 Markdown，这里整理一份常用语法速查，方便随时翻阅。

<!--more-->

## 标题

```markdown
# 一级标题
## 二级标题
### 三级标题
```

## 强调与列表

**粗体**、*斜体*、~~删除线~~。

1. 有序列表第一项
2. 有序列表第二项

- 无序列表项 A
- 无序列表项 B

## 表格

| 语法 | 用途 | 示例 |
|:-----|:-----|:-----|
| `#` | 标题 | `# 标题` |
| `**` | 粗体 | `**重要**` |
| `>` | 引用 | `> 引用内容` |

## 代码块

行内代码用反引号：`hugo server -D`。

围栏代码块支持语言高亮：

```go
func main() {
    fmt.Println("Hello, Hugo!")
}
```

## 引用

> 纸上得来终觉浅，绝知此事要躬行。
>
> —— 陆游《冬夜读书示子聿》

## 链接与图片

[Hugo 官网](https://gohugo.io)

![Hugo Logo](/images/hugo-logo.png)

## 任务列表

- [x] 学会标题语法
- [x] 学会列表语法
- [ ] 学会嵌入图片

## 数学公式

Hugo 的 goldmark 渲染器可以配合 KaTeX 显示数学公式：

行内公式 $E = mc^2$，块级公式：

$$
\int_{-\infty}^{+\infty} e^{-x^2}\\,dx = \sqrt{\pi}
$$

以上就是最常用的 Markdown 语法，祝你写作愉快 ✍️
