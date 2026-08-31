+++
title = "Hugo 写文章完整教程"
date = "2026-08-30"
draft = true
description = "从零开始学写博客文章：文件位置、front matter、Markdown 语法、主题特性（公式/目录/折叠块/图片）、预览与常见坑。"
tags = ["hugo", "教程", "markdown"]
categories = ["教程"]
toc = true
+++

这是一篇写给自己的写文章手册，也希望能帮到同样用 Hugo 的读者。内容覆盖：文章放哪、front matter 怎么写、Markdown 有哪些常用语法、本主题支持哪些特殊功能、以及怎么预览和避坑。

<!--more-->

## 一、文章文件放哪

所有文章都放在站点的 `content/posts/` 目录下，一个 `.md` 文件就是一篇文章：

```
content/
├── _index.md              ← 首页内容（显示在菜单上方）
├── about.md               ← 关于页（普通页面）
├── about-uyghur.md        ← 维吾尔语关于页
└── posts/                 ← 文章都放这里
    ├── hello-world.md
    ├── rich-content-test.md
    └── ...
```

**命名规则**：文件名就是网址的一部分。比如 `hello-world.md` → `https://你的域名/posts/hello-world/`。建议用小写英文 + 连字符，不要用中文名或空格。

## 二、front matter（文章头部信息）

每个 `.md` 文件的开头是 `+++` 包裹的 TOML 格式元数据，叫 front matter：

```toml
+++
title = "文章标题"                    # 必填：显示在列表和页面顶部
date = "2026-08-30"                  # 必填：发布日期（格式 年-月-日）
draft = false                        # 是否草稿：true=不发布（hugo 不带 -D 时不显示）
description = "一句话摘要"            # 可选：SEO 描述
tags = ["hugo", "教程"]              # 可选：标签（自动生成 /tags/ 页面）
categories = ["教程"]                # 可选：分类（自动生成 /categories/ 页面）
mathjax = true                       # 可选：true=启用 MathJax 数学公式
toc = true                           # 可选：true=文章顶部显示目录
+++
```

**必须有的只有两个**：`title` 和 `date`。其他都可选。

> ⚠️ 日期格式必须是 `2006-01-02` 这种（数字-数字-数字），否则会解析失败。

## 三、正文的基本写法

`+++` 结束之后就是正文，用 Markdown 写。最常用的语法：

### 标题（会自动进目录）

```markdown
# 一级标题（文章大标题，一般不用）
## 二级标题
### 三级标题
```

目录（toc）会收集二级和三级标题。

### 段落和强调

```markdown
这是一个普通段落。

**粗体** 和 *斜体*，还有 ~~删除线~~。
```

### 列表

```markdown
- 无序列表项
- 另一项
  - 嵌套项

1. 有序第一项
2. 有序第二项

- [x] 已完成的任务
- [ ] 待办任务
```

### 链接和图片

```markdown
[链接文字](https://example.com)

![图片说明](https://example.com/image.png)
```

图片可以用外部 URL，也可以放本地 `static/images/` 下然后写 `![图](images/xxx.png)`。

### 引用

```markdown
> 这是引用块，适合放名人名言或注意事项。
```

### 分割线

```markdown
---
```

### 表格

```markdown
| 列1 | 列2 |
|:----|:----|
| A   | 1   |
| B   | 2   |
```

## 四、代码块

### 带语言高亮的代码块

用三个反引号包起来，反引号后写语言名：

````markdown
```python
def hello():
    print("Hello, Hugo!")
```
````

支持的语言非常多：`python`、`go`、`bash`、`powershell`、`javascript`、`toml`、`markdown`、`html` 等。

### 行内代码

```markdown
用 `反引号` 包住的就是行内代码，比如 `hugo server -D`。
```

## 五、本主题的特殊功能

### 1. 数学公式（MathJax）

**第一步**：文章 front matter 里写 `mathjax = true`。

**第二步**：在正文里用 `$...$` 写行内公式，用 `$$...$$` 写块级公式：

```markdown
行内公式：$E = mc^2$

块级公式：
$$
\int_{-\infty}^{+\infty} e^{-x^2}\,dx = \sqrt{\pi}
$$
```

**⚠️ 两个坑**（我踩过的）：

1. **块级公式直接用 `$$`，不要用 shortcode**（`{{< texd >}}` 会把反斜杠双重转义，公式渲染失败）
2. **反斜杠命令要写双反斜杠**：`\,`（窄空格）在 Markdown 里会被吞反斜杠，必须写 `\\,` 才会正确输出 `\,`

### 2. 目录

front matter 写 `toc = true`，页面顶部自动生成目录（收集二、三级标题）。

### 3. 折叠块

```markdown
{{< details summary="点击展开" >}}
这里是被折叠的内容，支持 Markdown。
{{< /details >}}
```

想默认展开就加 `open="true"`：

```markdown
{{< details open="true" summary="默认展开" >}}
内容...
{{< /details >}}
```

### 4. 暗色模式下的图片

这个主题的暗色模式用 CSS `invert()` 反转颜色。黑白图片想跟随反转，加 `class="ioda"`：

```markdown
![黑白图](url){class="ioda"}
```

彩色图片不要加，反转后会很难看。

## 六、如何预览

在项目目录（`D:\Gheyret\gheyret.com`）打开终端：

```powershell
hugo server -D
```

- 浏览器打开 http://localhost:1313 就能看到
- 保存文件后浏览器**自动刷新**
- 按 `Ctrl+C` 停止

**`-D` 参数**：显示草稿（`draft = true` 的文章）。正式发布时不要加。

## 七、如何发布

写完并预览没问题后：

```powershell
hugo
```

会在 `public/` 目录生成完整静态网站，把这整个目录部署到 GitHub Pages / Cloudflare Pages / Netlify 即可上线。

## 八、写作流程建议

1. **复制模板**：复制一篇现有文章的 front matter 结构
2. **填标题和日期**：改 `title` 和 `date`
3. **写正文**：标题层级清晰（方便目录）、图文并茂
4. **预览**：`hugo server -D` 实时看效果
5. **改草稿状态**：确认无误后把 `draft` 改成 `false`
6. **发布**：`hugo` 编译 → 部署 `public/`

## 九、常见问题速查

| 问题 | 解决 |
|------|------|
| 文章不显示 | 检查 `draft` 是否为 false；预览时是否加了 `-D` |
| 日期显示异常 | 确认 front matter 的 `date` 是 `2026-08-30` 格式 |
| 公式不渲染 | 确认有 `mathjax = true`；块级公式别用 shortcode |
| 公式里 `\,` 消失 | 写成 `\\,` |
| 图片不显示 | 确认 URL 可访问；本地图放 `static/images/` |
| 目录没出现 | 确认有 `toc = true` 且正文有二级标题 |

---

记住最核心的一句话：**一篇新文章 = 一个 `content/posts/xxx.md` 文件 + front matter 填标题日期 + Markdown 正文**。就这么简单，写起来吧！✍️
