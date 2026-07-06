+++
title = 'Git 使用与 Markdown 博客写作入门'
date = 2026-07-06T16:30:00+08:00
draft = false
slug = 'git-markdown-blog-guide'
tags = ['Git', 'Markdown', 'Hugo']
categories = ['技术笔记']
+++

写技术博客不需要复杂工具。对我来说，先掌握两件事就够了：

- 用 Markdown 写内容
- 用 Git 提交和发布

这篇文章只记录最常用的流程。

## 写作流程

新建文章：

```powershell
hugo new content posts/my-note.md
```

编辑文章，把开头的草稿状态改成：

```toml
draft = false
```

本地预览：

```powershell
hugo server -D
```

确认没问题后提交：

```powershell
git add .
git commit -m "Add new blog post"
git push
```

推送后，GitHub Pages 会自动部署。

## 常用 Git 命令

查看修改：

```powershell
git status
```

加入提交：

```powershell
git add .
```

提交修改：

```powershell
git commit -m "Update blog"
```

推送到远程仓库：

```powershell
git push
```

查看提交记录：

```powershell
git log --oneline
```

## 常用 Markdown 语法

标题：

```markdown
# 一级标题
## 二级标题
### 三级标题
```

列表：

```markdown
- 第一项
- 第二项
- 第三项
```

代码块：

````markdown
```python
print("hello")
```
````

链接：

```markdown
[GitHub](https://github.com/)
```

引用：

```markdown
> 这是一段引用。
```

图片：

```markdown
![图片说明](/images/demo.png)
```

## 写作习惯

文件名建议使用英文、数字和短横线：

```text
2026-07-06-git-notes.md
2026-07-07-hugo-notes.md
```

标题可以写中文：

```toml
title = 'Git 常用命令整理'
```

每篇文章只写一个主题。内容不必长，重要的是清楚、可复用、以后还能看懂。
