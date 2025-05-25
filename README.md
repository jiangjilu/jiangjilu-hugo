# Hugo 博客项目，主题为 PaperMod，使用简体中文

---

````markdown
# 我的 Hugo 博客

本项目使用 [Hugo](https://gohugo.io/) 构建，采用简洁高效的 [PaperMod 主题](https://github.com/adityatelange/hugo-PaperMod)，适用于个人博客、技术分享、写作记录等场景。

---

## 🚀 快速开始

### 1. 克隆项目并初始化子模块

```bash
git clone https://github.com/yourusername/yourblog.git
cd yourblog
git submodule update --init --recursive
````

### 2. 安装 Hugo（需 extended 版）

可前往 [Hugo Releases](https://github.com/gohugoio/hugo/releases) 下载对应平台的 extended 版本。

### 3. 启动本地预览服务

```bash
hugo server -D --disableFastRender
```

* `-D` 表示显示草稿文章（draft）
* 默认访问地址：[http://localhost:1313](http://localhost:1313)

---

## ✍️ 内容创作

### 创建新文章

```bash
hugo new posts/我的第一篇文章.md
```

然后修改该文件的 Front Matter：

```toml
title = "我的第一篇文章"
date = 2025-05-25T12:00:00+08:00
draft = false
```

---

## 🛠️ 常用命令速查表

| 操作               | 命令                                                                                     |
| ---------------- | -------------------------------------------------------------------------------------- |
| 初始化新站点           | `hugo new site my-blog`                                                                |
| 添加主题（如 PaperMod） | `git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod` |
| 创建新文章            | `hugo new posts/xxx.md`                                                                |
| 启动本地预览           | `hugo server -D`                                                                       |
| 构建静态文件           | `hugo`                                                                                 |
| 清理 `public/` 目录  | `rm -rf public/`                                                                       |
| 更新子模块（主题）        | `git submodule update --remote --merge`                                                |
| 查看 Hugo 版本       | `hugo version`                                                                         |

---

## 🌐 网站部署

构建项目后，静态文件会输出到 `public/` 目录：

```bash
hugo
```

然后将 `public/` 下内容部署到任意支持静态站点的服务，如：

* GitHub Pages
* Netlify
* Cloudflare Pages ( 经实测 默认是使用 hugo 0.118.2, 可以在环境变量中指定版本为 `HUGO_VERSION=0.147.5` )
* 自建服务器 + Nginx

---

## 📄 robots.txt 配置（建议）

启用：

```toml
enableRobotsTXT = true
```

正式部署时，`robots.txt` 会自动生成：

```txt
User-agent: *
Disallow:
Sitemap: https://yourdomain.com/sitemap.xml
```

如需自定义，可创建文件：

```
layouts/robots.txt
```

---

## 📁 项目结构参考

```plaintext
content/
├── posts/               # 文章内容
│   └── my-first-post.md
├── about/               # 关于页面
layouts/
themes/
config.toml              # 配置文件
static/                  # 静态资源
```

---

## 🧑‍💻 贡献和维护

欢迎 Fork 或提交 PR，如果你有更好的内容结构或中文优化建议，欢迎讨论。

---

## 📜 许可协议

MIT License
