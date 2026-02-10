# Fluid Theme

一个简洁优雅的 Jekyll 博客主题，支持中文。

## 特性

- 响应式设计，移动端友好
- 代码语法高亮
- MathJax 数学公式支持
- SEO 优化（jekyll-seo-tag, sitemap）
- RSS 订阅（jekyll-feed）
- 标签分类系统
- 全文搜索

## 快速开始

### 1. 使用模板

```bash
# 克隆仓库
git clone https://github.com/yourusername/fluid-theme.git my-blog
cd my-blog

# 安装依赖
bundle install

# 本地预览
bundle exec jekyll serve
```

### 2. 配置站点

编辑 `_config.yml`：

```yaml
title: Your Blog Title
description: Your blog description
author: Your Name
url: "https://yourusername.github.io"
```

### 3. 创建文章

在 `_posts` 目录下创建 Markdown 文件，文件名格式：`YYYY-MM-DD-title.md`

```yaml
---
layout: post
title: "文章标题"
subtitle: "副标题（可选）"
date: 2026-01-01
tags: [标签1, 标签2]
description: "文章描述，用于 SEO"
---

文章内容...
```

### 4. 添加标签页

每个标签需要在 `tags` 目录下创建对应的 `.md` 文件：

```yaml
---
layout: tag
tag: 标签名
title: "标签名"
---
```

## 目录结构

```text
├── _config.yml      # 站点配置
├── _layouts/        # 布局模板
├── _posts/          # 文章目录
├── _includes/       # 可复用组件
├── assets/          # 静态资源
│   ├── css/         # 样式文件
│   └── images/      # 图片资源
├── tags/            # 标签页面
├── about.md         # 关于页面
├── privacy.md       # 隐私政策
└── search.html      # 搜索页面
```

## 封面图片

### 手动添加封面

在文章 front matter 中添加 `image` 字段：

```yaml
---
title: "文章标题"
image: /assets/images/posts/your-cover.png
---
```

### AI 自动生成封面（可选）

模板支持使用 Google Gemini API 自动为没有封面的文章生成图片。

**生成流程：**

1. 扫描 `_posts/` 目录下的所有文章
2. 检查 front matter 中是否已有 `image` 字段
3. 如果没有，调用 Gemini API 根据标题和描述生成封面
4. 保存图片到 `assets/images/posts/`
5. 自动更新文章 front matter 添加 `image` 字段

**本地使用：**

```bash
GEMINI_API_KEY=your_key node scripts/generate-covers.js
```

**CI 自动生成（默认关闭）：**

如需在 GitHub Actions 中自动生成封面：

1. 在仓库 Settings → Secrets 添加 `GEMINI_API_KEY`
2. 在仓库 Settings → Variables 添加 `ENABLE_AI_COVERS` 值为 `true`

## 部署

### GitHub Pages

1. 将仓库推送到 GitHub
2. 在 Settings → Pages 中选择 GitHub Actions 部署
3. 工作流文件已在 `.github/workflows/jekyll.yml` 中配置好

## License

本项目采用 [MIT License](LICENSE) 开源。

你可以自由地：

- 使用、复制、修改、合并、发布、分发本主题
- 用于个人或商业项目
但请保留原作者信息和许可证声明。