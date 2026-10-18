+++
title = 'Hugo 博客维护：搭建、写作与发布'
date = 2026-07-06T16:30:00+08:00
draft = false
hiddenInHomeList = true
searchHidden = true
slug = 'git-markdown-blog-guide'
aliases = ['/posts/2026/07/hello-hugo-papermod/']
description = '整理 Hugo + PaperMod 博客从本地运行、Markdown 写作到 Git 提交和 GitHub Pages 发布的完整流程。'
tags = ['Git', 'Markdown', 'Hugo', 'PaperMod', 'GitHub Pages']
categories = ['建站']
+++

这篇文章合并建站入门与 Git、Markdown 写作笔记，作为维护本站时可以反复查阅的操作指南。

本站使用 Hugo 生成静态页面，PaperMod 提供明暗模式、文章目录、搜索和代码复制等阅读功能，GitHub Actions 负责构建并部署到 GitHub Pages。

## 先运行本地网站

进入仓库根目录后，在 PowerShell 中运行：

```powershell
.\.tools\hugo\hugo.exe server -D
```

打开 <http://localhost:1313/> 查看效果，按 `Ctrl+C` 停止服务。`-D` 会显示草稿，正式构建默认不会发布草稿。

如果换一台电脑，应先克隆仓库、安装与部署配置一致的 Hugo Extended，再下载主题：

```powershell
git clone <repository-url> site
cd site
git clone --depth 1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
hugo server -D
```

独立安装 Hugo 并加入 `PATH` 后，可直接使用 `hugo` 命令。否则使用项目内的 `.\.tools\hugo\hugo.exe`，下文沿用本机工具路径。

## 新建一篇文章

```powershell
.\.tools\hugo\hugo.exe new content posts/my-note.md
```

文章保存在 `content/posts/`，默认使用仓库中的文章模板，并标记为草稿。先编辑文件开头的元数据：

```toml
+++
title = '文章标题'
date = 2026-07-10T10:00:00+08:00
draft = true
slug = 'my-note'
description = '用一两句话说明这篇文章解决的问题。'
tags = ['Git', 'Hugo']
categories = ['技术笔记']
+++
```

两个 `+++` 必须成对出现，正文从第二个标记之后开始。日期使用完整的 ISO 格式；`slug` 用来固定文章地址，之后修改标题时无需改变旧链接。

正文写完并完成预览后，把 `draft` 改为 `false`。`description` 用作文章摘要和页面描述，尽量说明具体问题与收获。

## 用 Markdown 组织正文

文章标题由元数据生成，正文通常从二级标题开始。

````markdown
## 背景

说明问题、使用场景和目标。

## 操作过程

1. 第一步。
2. 第二步。

- 补充条件。
- 注意事项。

**重点信息**可以加粗。

```powershell
git status
```

[参考资料](https://gohugo.io/)

![图片说明](/images/example.png)

> 引用或需要单独说明的结论。
````

图片示例要求仓库中存在 `static/images/example.png`。代码块写明语言，普通流程文本使用 `text`；不要把整段说明都放进代码块，以免影响阅读与自动摘要。

文章之间可以使用 Hugo 的 `relref` 短代码引用内容文件，减少文章地址变化造成的断链。写作时优先说明“问题、做法、结果”，删除重复段落和与主题无关的聊天内容。

## 构建与提交

先执行与部署接近的正式构建，确认文章元数据、模板和内部引用没有错误：

```powershell
.\.tools\hugo\hugo.exe --gc --minify
```

再检查并提交实际修改的文件：

```powershell
git status
git diff
git add content/posts/my-note.md
git commit -m "Add my note"
git push
```

`git add` 中的路径应替换为本次修改的文件。首次推送新分支时，根据 Git 提示设置远程跟踪分支。不要把生成的 `public/`、本地 `.tools/` 或下载的主题一起提交。

## GitHub Pages 发布

当前工作流监听 `main` 分支：

1. 将内容修改提交并推送；若在其他分支工作，先合并到 `main`。
2. 在 GitHub 的 Actions 页面检查构建和部署结果。
3. 部署成功后访问[wangyu 的博客](https://a1gernono.github.io/)确认内容。

仓库 `Settings → Pages → Source` 应选择 **GitHub Actions**。推送到任意分支都自动发布的说法不适用于本站当前配置。

如果本地有文章而线上没有，依次检查草稿状态、文章日期、推送分支和 Actions 执行结果。未来日期文章默认不会出现在正式构建中。

## 常用命令速查

| 目的 | 命令 |
| --- | --- |
| 查看当前分支 | `git branch --show-current` |
| 查看修改文件 | `git status` |
| 查看未暂存差异 | `git diff` |
| 查看已暂存差异 | `git diff --cached` |
| 查看最近提交 | `git log --oneline -5` |

新建文章、预览、正式构建、检查差异、提交发布，按这个顺序操作即可。日常无需反复修改网站结构，把主要精力留给内容本身。
