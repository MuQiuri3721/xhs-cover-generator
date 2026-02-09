# 小红书封面生成器

一个功能强大的小红书封面生成器，支持多种风格预设、自定义配色、字体选择等功能。

## 功能特性
- 🎨 11种预设风格（极简白、极客黑、科技蓝、奶油风、多巴胺、备忘录、复古风、未来感、小清新、商务灰、高级灰）
- ✏️ 实时预览和编辑
- 🖼️ 支持自定义背景图片
- 📦 一键打包下载高清图片
- � 配置保存到本地浏览器存储
- 📱 响应式设计
- 🌈 精美的渐变背景和动画效果

## 本地运行

### 方法1：直接打开
1. 克隆或下载项目
2. 直接在浏览器中打开 `index.html` 文件

### 方法2：使用本地服务器
```bash
# 使用 Python
python -m http.server 8000

# 使用 Node.js (需要先安装 http-server)
npx http-server

# 使用 PHP
php -S localhost:8000
```

然后在浏览器中访问 `http://localhost:8000`

## 在线部署

### Cloudflare Pages（推荐）
- 🚀 全球 CDN 加速，访问速度极快
- 💰 完全免费，无限流量和带宽
- 🌍 自动 HTTPS 证书
- 🔄 自动部署（连接 GitHub 后）

详细步骤请查看 [DEPLOYMENT.md](./DEPLOYMENT.md)

### GitHub Pages
- 🎯 直接集成在 GitHub 中
- 🆓 完全免费
- 📝 简单易用
- 🔗 自动 HTTPS

详细步骤请查看 [DEPLOYMENT.md](./DEPLOYMENT.md)

## 使用说明

### 创建封面
1. 在左侧编辑内容（标题、副标题、作者、日期、正文）
2. 选择风格预设或自定义样式
3. 上传背景图片（可选）
4. 实时预览效果
5. 点击"一键打包下载高清图"导出

### 配置管理
- 💾 保存配置：将当前样式设置保存到本地存储
- 📂 加载配置：从本地存储加载之前保存的配置
- 🔄 重置配置：恢复到默认设置

## 技术栈
- Vue 3 (CDN)
- Tailwind CSS (CDN)
- html2canvas (截图)
- JSZip (打包下载)
- Font Awesome (图标)

## 项目结构
```
小红书封面生成器/
├── index.html              # 主应用文件
├── README.md              # 项目说明
├── DEPLOYMENT.md          # 详细部署指南
├── QUICKSTART.md          # 快速开始指南
├── .github/
│   └── workflows/
│       └── deploy.yml    # GitHub Actions 自动部署配置
└── .gitignore            # Git 忽略文件
```

## 快速开始

查看 [QUICKSTART.md](./QUICKSTART.md) 了解如何快速部署到 Cloudflare Pages 或 GitHub Pages。

## 常见问题

### Q: 如何修改预设风格？
A: 在 `index.html` 中找到 `styles` 对象，修改相应的配置即可。

### Q: 支持哪些浏览器？
A: 支持所有现代浏览器（Chrome、Firefox、Safari、Edge）

### Q: 数据保存在哪里？
A: 所有配置保存在浏览器的本地存储中，刷新页面后数据会保留。

### Q: 如何自定义背景？
A: 点击"背景图片"部分上传图片，系统会自动应用并调整遮罩浓度。

## 许可证
MIT License

## 贡献
欢迎提交 Issue 和 Pull Request！

## 在线体验

- Cloudflare Pages: https://xhs-cover-generator.pages.dev
- GitHub Pages: https://mengyan070206.github.io/xhs-cover-generator/
