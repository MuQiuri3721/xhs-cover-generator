# 快速部署指南

## 🚀 三分钟快速部署

### 方式一：Cloudflare Pages（推荐）

1. **推送到 GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/xhs-cover-generator.git
   git branch -M main
   git push -u origin main
   ```

2. **连接 Cloudflare Pages**
   - 访问：https://dash.cloudflare.com/
   - 点击：Workers & Pages → Create application → Pages
   - 选择：Connect to Git → Connect GitHub
   - 选择仓库：xhs-cover-generator
   - 点击：Begin setup → Save and Deploy

3. **完成！**
   - 访问：https://xhs-cover-generator.pages.dev
   - 全球 CDN，无限流量，完全免费

---

### 方式二：GitHub Pages

1. **推送到 GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/xhs-cover-generator.git
   git branch -M main
   git push -u origin main
   ```

2. **启用 GitHub Pages**
   - 进入仓库：Settings → Pages
   - Source 选择：Deploy from a branch
   - Branch 选择：main → /(root)
   - 点击：Save

3. **完成！**
   - 访问：https://YOUR_USERNAME.github.io/xhs-cover-generator/
   - 自动 HTTPS，完全免费

---

## 📝 详细部署指南

查看 [DEPLOYMENT.md](./DEPLOYMENT.md) 获取详细的部署说明和配置选项。

## ✨ 推荐选择

**Cloudflare Pages** 是最佳选择，因为：
- ⚡ 全球 CDN 加速
- 💰 无限流量和带宽
- 🚀 部署速度更快
- 🌍 全球访问体验更好

## 🔄 更新网站

只需推送代码即可自动部署：
```bash
git add .
git commit -m "Update content"
git push
```

两个平台都会自动检测并重新部署！
