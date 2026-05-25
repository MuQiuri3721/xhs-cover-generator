# 小红书封面生成器

> 一键生成小红书爆款封面，支持 36+ 风格预设、背景图片、文字特效、二维码水印

## 功能特性

- 🎨 **36+ 预设风格**：基础风格、渐变风格、字体风格、特效风格、节日风格、行业风格
- ✏️ **实时预览编辑**：标题、副标题、作者、日期、正文
- 🖼️ **背景图片上传**：支持拖放 + 滤镜调节（亮度/对比度/饱和度/灰度/模糊）
- 📐 **精确尺寸**：360×480px（3:4 小红书标准比例）
- 🔤 **18 种中英文字体**：思源黑体、衬线体、手写体、卡通体、书法体
- ✨ **文字特效**：阴影、描边、渐变、竖排文字
- 📦 **一键打包下载**：ZIP 格式高清 PNG（2x 分辨率）
- 💾 **配置保存**：localStorage 持久化，可保存/加载模板
- 📱 **三种预览模式**：桌面 / 手机 / 平板
- 🔲 **二维码生成**：可嵌入封面
- 💧 **水印设置**：位置/大小/透明度
- 📝 **文案助手**：标题/开场白/标签模板，关键词替换

## 技术栈

- Vue 3 (CDN)
- Tailwind CSS (CDN)
- html2canvas（图片导出）
- JSZip（ZIP 打包）
- QRCode.js（二维码生成）

## 本地运行

### 方法 1：直接打开
双击 `index.html` 在浏览器中打开

### 方法 2：本地服务器
```bash
# Python
python -m http.server 8000

# Node.js
npx http-server -p 8000
```
访问 `http://localhost:8000`

## 在线部署

### Cloudflare Pages（推荐）
1. 推送代码到 GitHub
2. 连接 Cloudflare Pages → 选择仓库 → 部署
3. 获得 `https://xhs-cover-generator.pages.dev`

### GitHub Pages
1. 推送代码到 GitHub
2. Settings → Pages → Source: main / (root)
3. 获得 `https://MuQiuri3721.github.io/xhs-cover-generator/`

## 文件结构

```
小红书封面生成器/
├── index.html          # 主应用（单文件，可直接打开）
├── README.md           # 项目说明
├── DEPLOYMENT.md       # 详细部署指南
├── QUICKSTART.md       # 快速开始
├── .github/
│   └── workflows/
│       └── deploy.yml  # GitHub Actions 自动部署
└── .gitignore
```

## 许可证

MIT License