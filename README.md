<div align="center">
  <img src="./public/logo.png" alt="ThisCover Logo" width="120" height="120">
  
  # ThisCover
  
  <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; margin: 20px 0;">
    <a href="https://go.202597.xyz"><img src="https://img.shields.io/badge/Deployed_with-EdgeOne_Pages-0070f3?style=flat-square&logo=cloudflare&logoColor=white" alt="EdgeOne Pages"></a>
    <a href="https://nextjs.org/"><img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white" alt="Next.js"></a>
    <a href="https://reactjs.org/"><img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React"></a>
    <a href="https://tailwindcss.com/"><img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white" alt="Tailwind CSS"></a>
    <a href="https://shadcn/ui"><img src="https://img.shields.io/badge/shadcn/ui-000000?style=flat-square&logo=shadcnui&logoColor=white" alt="shadcn/ui"></a>
    <a href="https://vercel.com/"><img src="https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white" alt="Vercel"></a>
    <a href="https://netlify.com/"><img src="https://img.shields.io/badge/Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white" alt="Netlify"></a>
  </div>
  
  一个免费、漂亮的封面生成器，基于 [**rutikwankhade/CoverView**](https://github.com/rutikwankhade/CoverView)
</div>

全新架构升级，使用 `next.js v16` + `react v19` + `shadcn/ui` + `tailwindcss v4` + `lucide icons`

在原来的基础上进行了汉化 + 本土功能定制和扩展

## 🎨 核心功能

### 封面设计
- 📐 多种尺寸比例：支持 1:1、16:9、4:3 等 9+ 种常用比例
- 🎭 丰富主题模板：提供 18+ 种精美主题，包括桌面、手机、现代等风格
- 🖼️ 背景选项：支持单色、渐变、上传图片和在线图片
- 🎯 图标支持：支持上传自定义图标和搜索 Iconify 图标库
- ✍️ 字体选择：内置 29+ 种开源/免费商用字体
- 🎨 纹理效果：支持多种纹理背景，可与纯色和渐变背景结合

### 导出功能
- 📤 多种格式：支持 PNG、JPG、WebP 格式导出
- 🔍 放大倍数：支持 0.5-5 倍图片放大导出
- 📋 复制到剪贴板：一键复制生成的图片到剪贴板
- 💾 本地保存：将配置信息存储到本地浏览器，方便后续使用

### 用户体验
- 🏠 直观首页：展示功能介绍、常见问题和封面示例
- 🔄 实时预览：编辑过程中实时预览效果
- 📱 响应式设计：完美适配桌面端和移动端
- 🌙 深色模式：支持深色/浅色主题切换
- 🎯 一键使用：首页示例支持一键应用到编辑器

## 📦 快速开始

### 前提条件
- Node.js >= 18.18.0
- pnpm (推荐) 或 npm/yarn

### 安装与运行

```bash
# 克隆仓库
git clone https://github.com/mkboy95/cover.git
cd cover

# 安装依赖
pnpm install

# 启动开发服务器
pnpm dev

# 构建生产版本
pnpm build
```

### 环境变量

创建 `.env` 文件，添加以下内容：

```txt
NEXT_PUBLIC_API_ACCESS_KEY = 'xxxxx'  # Unsplash API 密钥
NEXT_PUBLIC_API_ICONIFY_URL = 'https://api.iconify.design'
# Cloudflare Analytics，不用请注释 src/app/layout.tsx 中的 Script
NEXT_PUBLIC_CLOUDFLARE_ANALYTICS_TOKEN = 'xxxxx'
```

> 📝 如何获取 Unsplash API Key：
> 1. 访问 [Unsplash Developers](https://unsplash.com/developers)
> 2. 注册或登录账号
> 3. 创建一个新的应用
> 4. 获取 API 访问密钥

## 🚀 部署

### EdgeOne Pages 部署

本项目支持在 EdgeOne Pages 上免费部署，详细部署指南请查看 [DEPLOY.md](DEPLOY.md) 文件。

### 其他部署选项
- Vercel
- Netlify
- GitHub Pages
- 任何支持 Next.js 的静态网站托管服务

## 📁 项目结构

```
├── public/            # 静态资源
├── src/              # 源代码
│   ├── app/          # Next.js App Router
│   │   ├── components/   # 应用组件
│   │   ├── settings/     # 配置文件
│   │   ├── themes/       # 主题模板
│   │   └── editor/       # 编辑器页面
│   ├── components/   # UI 组件
│   └── lib/          # 工具函数
├── .gitignore        # Git 忽略文件
├── LICENSE           # 许可证
├── README.md         # 项目说明
├── DEPLOY.md         # 部署指南
├── next.config.ts    # Next.js 配置
├── package.json      # 项目依赖
└── tsconfig.json     # TypeScript 配置
```

## 🎯 技术栈

- **前端框架**：Next.js 16, React 19
- **UI 组件**：shadcn/ui, Tailwind CSS 4
- **图标库**：Lucide Icons
- **状态管理**：React Context API
- **图片处理**：html2canvas-pro
- **API 集成**：Unsplash API, Iconify API

## 🌟 特色亮点

- 🎨 现代化 UI 设计，支持深色模式
- 🚀 高性能，快速加载和渲染
- 📱 响应式布局，适配各种设备
- 🔧 丰富的自定义选项
- 📤 多种导出格式和选项
- 💾 本地存储配置，提升用户体验
- 🌍 完全汉化，适合中文用户

## 🤝 贡献

欢迎贡献代码、报告 bug 或提出新功能建议！

1. Fork 本仓库
2. 创建 feature 分支
3. 提交更改
4. 推送到分支
5. 打开 Pull Request

## 📄 许可证

本项目基于 MIT 许可证开源。

## 🔗 相关链接

- **项目主页**：[ThisCover](https://github.com/mkboy95/cover)
- **部署指南**：[DEPLOY.md](DEPLOY.md)
- **超赞博客**：[https://go.202597.xyz](https://go.202597.xyz)
- **原项目**：[CoverView](https://github.com/rutikwankhade/CoverView)

## 📞 支持

如果您在使用过程中遇到问题，可以：

1. 查看 [DEPLOY.md](DEPLOY.md) 部署指南
2. 在 GitHub 仓库中提交 Issue
3. 访问 [超赞博客](https://go.202597.xyz) 获取更多资源

---

> 🎉 感谢使用 ThisCover！希望它能帮助您创建出精美的封面图片。
