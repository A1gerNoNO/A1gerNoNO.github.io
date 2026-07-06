# Hugo + Ivy Personal Site

这是一个使用 Hugo 和 Ivy 主题搭建的 GitHub Pages 个人网站模板。

## 使用前需要替换

在以下文件中替换占位内容：

- `hugo.toml`
  - `YOUR_USERNAME`
  - `YOUR_NAME`
- `content/_index.md`
  - `YOUR_USERNAME`
  - `YOUR_NAME`
- `content/about.md`
  - `YOUR_USERNAME`
  - `YOUR_NAME`

如果你的 GitHub 用户名是 `alice`，仓库名应为：

```text
alice.github.io
```

网站地址将是：

```text
https://alice.github.io/
```

## GitHub Pages 设置

进入仓库：

```text
Settings -> Pages -> Build and deployment -> Source -> GitHub Actions
```

之后每次推送到 `main` 分支，GitHub Actions 会自动构建并部署网站。

## 本地预览

安装 Hugo Extended 后运行：

```powershell
git clone https://github.com/yihui/hugo-ivy.git themes/hugo-ivy
hugo server -D
```

浏览器打开：

```text
http://localhost:1313/
```

## 新建文章

```powershell
hugo new content posts/new-post.md
```

把文章 front matter 中的 `draft` 改成 `false` 后，提交并推送即可发布。
