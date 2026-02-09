# 部署指南

本指南介绍如何将小红书封面生成器部署到 Cloudflare Pages 和 GitHub Pages。

## 方案一：Cloudflare Pages 部署（推荐）

### 优势
- 🚀 全球 CDN 加速，访问速度极快
- 💰 完全免费，无限流量和带宽
- 🌍 自动 HTTPS 证书
- 🔄 自动部署（连接 GitHub 后）
- 📦 自定义域名支持

### 步骤 1：准备代码

1. 确保项目文件结构正确：
   ```
   小红书封面生成器/
   ├── index.html
   ├── .gitignore
   └── README.md
   ```

2. 初始化 Git 仓库（如果还没有）：
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

### 步骤 2：推送到 GitHub

1. 在 GitHub 创建新仓库（例如：xhs-cover-generator）
2. 推送代码到 GitHub：
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/xhs-cover-generator.git
   git branch -M main
   git push -u origin main
   ```

### 步骤 3：连接 Cloudflare Pages

1. 访问 [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. 登录或注册账号
3. 点击左侧菜单的 **Workers & Pages**
4. 点击 **Create application** → **Pages** 标签页
5. 选择 **Connect to Git**

### 步骤 4：授权 GitHub

1. 点击 **Connect GitHub** 按钮
2. 如果是第一次，需要授权 Cloudflare 访问你的 GitHub
3. 选择你的仓库：`xhs-cover-generator`
4. 点击 **Begin setup**

### 步骤 5：配置构建设置

Cloudflare Pages 会自动检测到这是静态站点，配置如下：

```
Project name: xhs-cover-generator
Production branch: main
Build command: (留空)
Build output directory: / (根目录)
```

点击 **Save and Deploy**

### 步骤 6：等待部署

部署通常需要 1-3 分钟，完成后会显示：
- 访问地址：`https://xhs-cover-generator.pages.dev`
- 自动 HTTPS：✅
- 全球 CDN：✅

### 步骤 7：自定义域名（可选）

1. 在 Cloudflare Pages 项目设置中
2. 点击 **Custom domains**
3. 添加你的域名（如：xhs.yourdomain.com）
4. 按照提示配置 DNS 记录

### 自动部署

连接 GitHub 后，每次推送代码到 main 分支，Cloudflare Pages 会自动重新部署。

---

## 方案二：GitHub Pages 部署

### 优势
- 🎯 直接集成在 GitHub 中
- 🆓 完全免费
- 📝 简单易用
- 🔗 自动 HTTPS

### 步骤 1：推送到 GitHub

1. 在 GitHub 创建新仓库
2. 推送代码：
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/xhs-cover-generator.git
   git branch -M main
   git push -u origin main
   ```

### 步骤 2：启用 GitHub Pages

1. 进入仓库页面
2. 点击 **Settings** 标签
3. 在左侧菜单找到 **Pages**
4. 在 **Build and deployment** 部分：
   - Source 选择：**Deploy from a branch**
   - Branch 选择：**main**
   - Folder 选择：**/(root)**
5. 点击 **Save**

### 步骤 3：等待部署

几分钟后，你的网站会部署到：
```
https://YOUR_USERNAME.github.io/xhs-cover-generator/
```

### 步骤 4：自定义域名（可选）

1. 在 Pages 设置中，点击 **Custom domain**
2. 添加你的域名
3. 配置 DNS 记录：
   - 类型：CNAME
   - 名称：xhs（或你想要的子域名）
   - 值：YOUR_USERNAME.github.io

---

## 方案三：GitHub Actions 自动部署到 GitHub Pages

### 优势
- 🔄 自动化部署流程
- 📦 构建步骤可自定义
- 🎯 推送代码即自动部署

### 步骤 1：创建 GitHub Actions 工作流

项目已包含 `.github/workflows/deploy.yml` 文件，内容如下：

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Pages
        uses: actions/configure-pages@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### 步骤 2：启用 GitHub Pages

1. 进入仓库 **Settings** → **Pages**
2. Source 选择：**GitHub Actions**

### 步骤 3：推送代码触发部署

```bash
git add .
git commit -m "Update website"
git push
```

GitHub Actions 会自动运行并部署网站。

---

## 两种方案对比

| 特性 | Cloudflare Pages | GitHub Pages |
|------|----------------|--------------|
| 速度 | ⚡ 极快（全球 CDN） | 🚀 快 |
| 流量限制 | 无限制 | 100GB/月 |
| 带宽限制 | 无限制 | 无限制 |
| 自定义域名 | ✅ 免费 | ✅ 免费 |
| 自动部署 | ✅ 支持 | ✅ 支持 |
| 构建时间 | 无限制 | 10分钟/次 |
| 访问地址 | xxx.pages.dev | xxx.github.io |

## 推荐方案

**推荐使用 Cloudflare Pages**，原因：
1. 🌍 全球 CDN 加速，访问速度更快
2. 💰 完全免费，无流量限制
3. 🚀 部署速度更快
4. 🔄 自动部署体验更好

## 常见问题

### Q: Cloudflare Pages 需要付费吗？
A: 完全免费，包括无限流量和带宽。

### Q: 可以同时部署到两个平台吗？
A: 可以，同一个仓库可以同时连接 Cloudflare Pages 和 GitHub Pages。

### Q: 如何更新网站？
A: 只需推送代码到 GitHub，两个平台都会自动部署。

### Q: 支持自定义域名吗？
A: 两个平台都支持，需要你有自己的域名。

### Q: 部署后可以修改吗？
A: 可以，随时修改代码并推送，会自动重新部署。

## 下一步

选择一个方案开始部署吧！如果遇到问题，请查看各平台的官方文档或寻求帮助。
