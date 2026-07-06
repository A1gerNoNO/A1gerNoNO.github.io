+++
title = 'Git 使用与 Markdown 博客写作入门'
date = 2026-07-06T16:30:00+08:00
draft = false
slug = 'git-markdown-blog-guide'
tags = ['Git', 'Markdown', 'Hugo', '博客']
categories = ['技术笔记']
+++

我打算把这个网站作为长期技术博客使用。对这种写作方式来说，最需要掌握的不是复杂前端，而是两个基础工具：Git 和 Markdown。

Git 负责版本管理和发布，Markdown 负责写文章。只要这两个东西用顺手，写博客就会变成一个很轻的日常动作。

## 一、日常写博客的基本流程

我的站点目录是：

```powershell
D:\Codex_project\hugo-ivy-site
```

每天写新文章时，先进入站点目录：

```powershell
cd D:\Codex_project\hugo-ivy-site
```

然后新建文章：

```powershell
.\.tools\hugo\hugo.exe new content posts/2026-07-06-my-note.md
```

文章会生成在：

```text
content/posts/2026-07-06-my-note.md
```

写完之后本地预览：

```powershell
.\.tools\hugo\hugo.exe server -D
```

浏览器打开：

```text
http://127.0.0.1:1313/
```

确认内容没问题后，提交并推送：

```powershell
git add .
git commit -m "Add daily tech note"
git push
```

GitHub Actions 会自动构建网站。构建成功后，文章就会出现在：

```text
https://a1gernono.github.io/
```

## 二、Git 最常用命令

技术博客不需要一开始学完整的 Git。先会下面几个命令就够用。

查看当前改了什么：

```powershell
git status
```

把所有修改加入提交：

```powershell
git add .
```

提交修改：

```powershell
git commit -m "Update blog"
```

推送到 GitHub：

```powershell
git push
```

查看提交历史：

```powershell
git log --oneline
```

如果每天只写文章，最常用的就是这三行：

```powershell
git add .
git commit -m "Add new blog post"
git push
```

## 三、Markdown 基础语法

Markdown 是一种轻量写作格式，很适合技术博客。

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

有序列表：

```markdown
1. 第一步
2. 第二步
3. 第三步
```

加粗和行内代码：

```markdown
**重要内容**

`git status`
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

## 四、Hugo 文章开头的配置

Hugo 文章开头通常会有一段 front matter：

```toml
+++
title = 'Git 使用与 Markdown 博客写作入门'
date = 2026-07-06T21:00:00+08:00
draft = false
tags = ['Git', 'Markdown']
categories = ['技术笔记']
+++
```

其中最重要的是：

```toml
draft = false
```

如果是：

```toml
draft = true
```

文章只会在本地预览时出现，不会发布到线上。

## 五、建议的文章命名方式

文件名建议使用英文、数字和短横线：

```text
2026-07-06-git-notes.md
2026-07-07-hugo-notes.md
2026-07-08-python-env.md
```

标题可以继续写中文：

```toml
title = 'Git 常用命令整理'
```

这样 URL 更干净，也更不容易出编码问题。

## 六、我准备采用的写作方式

这个博客会尽量保持极简。

首页只保留文章名，不放复杂介绍。文章内部保持清楚的层级，用标题、列表和代码块组织内容。

我希望写作流程尽量轻：

1. 新建 Markdown 文件。
2. 写下当天学到的内容。
3. 本地预览。
4. Git 提交并推送。
5. GitHub Pages 自动发布。

长期来看，博客不是一次性装修出来的，而是靠每天一点点积累出来的。
