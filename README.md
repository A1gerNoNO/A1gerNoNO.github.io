# wangyu 个人主页

这是 [wangyu.github.io](https://wangyu.github.io/) 的 Hugo 源文件，使用 PaperMod 主题并通过 GitHub Actions 部署。

当前主页只展示个人资料、真名和联系方式；文章源文件保留在 `content/posts/`，但不会出现在首页、搜索、归档或导航中。

## 本地预览

仓库已包含 Hugo Extended 和主题，直接在项目根目录运行：

```powershell
.\.tools\hugo\hugo.exe server -D
```

打开 <http://localhost:1313/> 查看页面，按 `Ctrl+C` 停止预览。

如果本机已安装 Hugo，也可以运行：

```powershell
hugo server -D
```

## 构建与发布

正式构建：

```powershell
hugo --gc --minify
```

推送到 `main` 后，GitHub Actions 会自动构建并发布网站。发布前请确认页面内容和移动端布局正常。

## 目录说明

- `hugo.toml`：站点信息、主页链接、导航和搜索设置。
- `content/_index.md`：主页资料内容。
- `content/about.md`：关于页和联系方式。
- `content/posts/`：保留的文章源文件。
- `assets/css/extended/custom.css`：站点自定义样式。
- `.github/workflows/`：自动构建与部署配置。

`public/`、`resources/_gen/`、`themes/PaperMod/` 和 `.tools/` 属于生成内容或本地工具，除非确有需要，不要手动修改生成文件。
