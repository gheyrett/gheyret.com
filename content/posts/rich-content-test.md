+++
title = "复合内容测试：图片、公式、代码、表格全都有"
date = "2026-08-30"
draft = false
description = "一篇用于测试主题渲染能力的复合文章：外部图片、MathJax 公式、代码高亮、表格、引用、折叠块、目录。"
tags = ["测试", "markdown", "mathjax"]
categories = ["测试"]
mathjax = true
toc = true
+++

这篇文章用来测试 no-style-please 主题对各种内容的渲染效果：图片、公式、代码、表格、引用、折叠块等。

<!--more-->

## 一、外部图片

**测试 1：普通图片（外部 URL）**

![测试图片 1](https://picsum.photos/seed/blog1/640/400)

**测试 2：带标题的图片**

![测试图片 2](https://picsum.photos/seed/blog2/640/400)

**测试 3：小尺寸图片**

![小图](https://picsum.photos/seed/blog3/200/200)

![小图](images/avatar.png)


> 💡 这个主题的暗色模式用 CSS `invert()` 反转颜色，彩色图片默认不反转。如果图片是黑白风格想跟随反转，可以加 `class="ioda"`：`![图](url){class="ioda"}`。

## 二、数学公式（MathJax）

**行内公式**：爱因斯坦质能方程是 $E = mc^2$，或者用短代码写：{{< texi "a^2 + b^2 = c^2" >}}。

**块级公式**（直接用 `$$`，避免 shortcode 反斜杠转义问题）：

$$
\int_{-\infty}^{+\infty} e^{-x^2}\\,dx = \sqrt{\pi}
$$

**另一个块级公式**（直接用 `$$`）：

$$
\frac{d}{dx}\left( \int_{a}^{x} f(t)\,dt \right) = f(x)
$$

**多行公式**（对齐）：

$$
\begin{aligned}
(x+1)^2 &= x^2 + 2x + 1 \\
(x-1)^2 &= x^2 - 2x + 1
\end{aligned}
$$

## 三、代码块

**PowerShell 代码：**

```powershell
# 启动 Hugo 开发服务器
hugo server -D
```

**Python 代码：**

```python
def fibonacci(n):
    """返回斐波那契数列的前 n 项"""
    a, b = 0, 1
    result = []
    for _ in range(n):
        result.append(a)
        a, b = b, a + b
    return result

print(fibonacci(10))  # [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

**Go 代码：**

```go
package main

import "fmt"

func main() {
    msg := "Hello, Hugo!"
    fmt.Println(msg)
}
```

**行内代码**：`fmt.Println()`、`hugo server -D`、`{{ .Title }}`。

## 四、表格

| 功能 | 支持情况 | 备注 |
|:------|:--------|:-----|
| 外部图片 | ✅ | 任意 URL |
| MathJax 公式 | ✅ | 需 `mathjax = true` |
| 代码高亮 | ✅ | Hugo 内置 Chroma |
| 表格 | ✅ | 标准 Markdown |
| 折叠块 | ✅ | details 短代码 |
| 目录 | ✅ | 需 `toc = true` |

## 五、引用块

> 极简不是简陋，而是把注意力还给内容本身。
>
> —— 某位不知名的博客作者

嵌套引用：

> 外层引用
>
> > 内层引用，用来测试嵌套渲染效果。

## 六、列表

**无序列表：**

- 第一项
- 第二项
  - 嵌套项 A
  - 嵌套项 B
- 第三项

**有序列表：**

1. 第一步：写文章
2. 第二步：编译站点
3. 第三步：部署上线

**任务列表：**

- [x] 测试图片
- [x] 测试公式
- [ ] 测试折叠块（见下方）
- [ ] 全部通过后发布

## 七、折叠块（details）

{{< details summary="点击展开：这是一段折叠内容" >}}
这里的内容默认是隐藏的，点击 summary 才展开。可以用来放"剧透"、额外说明、或长代码。

还可以**嵌套 Markdown**：列表、公式、代码都行。

```bash
echo "折叠块里的代码"
```
{{< /details >}}

{{< details open="true" summary="默认展开的折叠块" >}}
这个折叠块设置了 `open="true"`，所以页面加载时就展开。
{{< /details >}}

## 八、水平分割线

上面有两条分割线（`---`），这个主题把分割线渲染成 `/////` 样式。

---

文章结束。如果以上所有内容都正常渲染，说明这个主题的基本功是完整的。🎉
