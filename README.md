# wangyu 的个人博客

使用 Hugo + PaperMod 构建，部署到 <https://wangyu.github.io/>。

## 本地运行

安装 Hugo Extended **0.163.3**（与 GitHub Actions 一致），然后在 PowerShell 中运行：

```powershell
cd E:\Workbench\alger.github.io
git clone --depth 1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
hugo server -D
```

主题只需下载一次。打开 <http://localhost:1313/> 预览；`Ctrl+C` 停止服务。

本次恢复的本机目录已包含主题和 `.tools/hugo/hugo.exe`，无需重复下载，可直接运行：

```powershell
cd E:\Workbench\alger.github.io
.\.tools\hugo\hugo.exe server -D
```

## 写文章

```powershell
hugo new content posts/my-note.md
```

新文章使用 `archetypes/posts.md`，默认为草稿。编辑标题、标签和正文，确认后把 `draft` 改为 `false`。`description` 可填写简短摘要，也用于搜索引擎描述。

文章放在 `content/posts/`。当前个人主页默认隐藏文章；文章源文件仍保留，给每篇文章加上 `searchHidden = false` 并恢复导航后即可重新公开。Front matter 用一对 `+++` 包围；日期使用 ISO 格式，例如 `2026-07-10T10:00:00+08:00`。

## 检查和发布

```powershell
hugo --gc --minify
git status
git add content hugo.toml assets archetypes layouts
git commit -m "Update blog"
git push
```

只有推送到 `main` 才会自动部署；其他分支需先合并。GitHub 仓库 `Settings → Pages → Source` 应设为 **GitHub Actions**。

`public/`、`resources/_gen/`、`themes/PaperMod/` 和 `.tools/` 是生成内容或本地工具，不提交。

## 网站结构

- `hugo.toml`：站点信息、导航、RSS、搜索 JSON 和阅读设置。
- `assets/css/extended/custom.css`：列表、正文及移动端样式。
- `content/about.md`：关于页。
- `content/search.md`：PaperMod 原生本地搜索，无第三方服务。
- `content/archives.md`：文章归档。
- `layouts/index.json`：搜索索引，每次构建独立生成以避免预览重建时出现重复条目。
- `.github/workflows/`：构建与部署。

保留已有文章 URL 规则：`/posts/:year/:month/:slug/`。

## 内容整理

目前保留三篇主题完整的文章：商城需求与业务流程、DDD 建模与工程分层、Hugo 博客搭建与写作发布。原 DDD 建模、工程模型和建站入门文章通过 `aliases` 跳转到对应合并文章，原有主要文章通过显式 `slug` 保持地址稳定。

网页显示名称统一为“wangyu”；域名、仓库地址和 GitHub 链接仍使用真实账号 `A1gerNoNO`。
