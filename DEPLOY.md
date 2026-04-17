# EdgeOne Pages 部署指南

## 🚀 快速部署

本指南将帮助您在 EdgeOne Pages 上部署 ThisCover 项目。EdgeOne Pages 是一个免费、高效的静态网站托管平台，适合部署 Next.js 应用。

## 📋 前提条件

- **EdgeOne 账号**：访问 [EdgeOne 官网](https://edgeone.app/) 注册免费账号
- **GitHub 账号**：用于代码托管和自动部署
- **Unsplash API Key**：用于获取图片资源（可选，详见下方配置说明）

## 🛠️ 部署步骤

### 1. 准备代码

确保您的代码已推送到 GitHub 仓库。如果还没有，可以使用以下命令初始化仓库：

```bash
# 初始化 git 仓库
git init

# 添加远程仓库
git remote add origin https://github.com/your-username/cover.git

# 提交代码
git add .
git commit -m "Initial commit"
git push -u origin main
```

### 2. 配置 EdgeOne Pages

1. **登录 EdgeOne 控制台**
   - 访问 [EdgeOne 控制台](https://console.cloud.tencent.com/edgeone)
   - 登录您的账号

2. **创建 Pages 项目**
   - 导航到 "Pages" 服务
   - 点击 "创建项目" 按钮
   - 选择 "从 Git 仓库导入"

3. **连接 GitHub 仓库**
   - 授权 EdgeOne 访问您的 GitHub 账号
   - 选择包含 ThisCover 项目的仓库
   - 选择要部署的分支（建议使用 `main`）

4. **配置构建参数**
   - **框架预设**：选择 `Next.js`
   - **根目录**：`./`
   - **输出目录**：`.next`
   - **构建命令**：`pnpm run build`
   - **安装命令**：`pnpm install`

   > 🔧 如果您使用 npm 或 yarn，请相应修改构建和安装命令：
   > - npm: `npm install` 和 `npm run build`
   > - yarn: `yarn install` 和 `yarn build`

5. **配置环境变量**
   - 在 "环境变量" 部分添加以下变量：

   | 环境变量 | 值 | 描述 |
   |---------|-----|------|
   | `NEXT_PUBLIC_API_ACCESS_KEY` | `your-unsplash-api-key` | Unsplash API 访问密钥（可选） |
   | `NEXT_PUBLIC_API_ICONIFY_URL` | `https://api.iconify.design` | Iconify API URL（默认值） |
   | `NEXT_PUBLIC_CLOUDFLARE_ANALYTICS_TOKEN` | `your-cloudflare-token` | Cloudflare 分析令牌（可选） |

   > 📝 如何获取 Unsplash API Key：
   > 1. 访问 [Unsplash Developers](https://unsplash.com/developers)
   > 2. 注册或登录账号
   > 3. 创建一个新的应用
   > 4. 获取 API 访问密钥

6. **部署项目**
   - 点击 "部署" 按钮
   - 等待部署完成（通常需要 1-3 分钟）

### 3. 验证部署

1. **查看部署状态**
   - 在 EdgeOne Pages 控制台查看部署进度
   - 部署完成后，会显示 "部署成功" 状态

2. **访问网站**
   - EdgeOne Pages 会为您的项目分配一个默认域名，格式为 `your-project.edgeone.app`
   - 点击域名链接，验证网站是否正常运行

3. **配置自定义域名（可选）**
   - 在项目设置中，找到 "域名管理"
   - 添加您的自定义域名
   - 按照提示配置 DNS 记录

## 📁 项目结构

```
├── public/            # 静态资源
├── src/              # 源代码
│   ├── app/          # Next.js App Router
│   ├── components/   # UI 组件
│   └── lib/          # 工具函数
├── .gitignore        # Git 忽略文件
├── LICENSE           # 许可证
├── README.md         # 项目说明
├── next.config.ts    # Next.js 配置
├── package.json      # 项目依赖
└── tsconfig.json     # TypeScript 配置
```

## ⚙️ 构建配置

### Next.js 配置

项目使用 Next.js 16，配置如下：

```typescript
// next.config.ts
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  devIndicators: false,
  images: {
    unoptimized: true,
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'p.weizwz.com',
        port: '',
        pathname: '/**'
      },
      {
        protocol: 'https',
        hostname: 'images.unsplash.com',
        port: '',
        pathname: '/**'
      }
    ]
  }
}

export default nextConfig
```

### 构建命令

项目使用 `pnpm` 作为包管理器，构建命令如下：

```json
// package.json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  }
}
```

## 📚 常见问题

### Q: 部署失败，提示 `NEXT_PUBLIC_API_ACCESS_KEY is not defined`

**A:** 这是因为缺少 Unsplash API 访问密钥。您有两个选择：
1. 在 EdgeOne Pages 中配置 `NEXT_PUBLIC_API_ACCESS_KEY` 环境变量
2. 修改代码，在没有 API 密钥时使用默认值或禁用相关功能

### Q: 部署成功但图片无法加载

**A:** 检查以下几点：
1. 确保 Unsplash API 密钥配置正确
2. 检查网络连接是否正常
3. 确认 `next.config.ts` 中的 `remotePatterns` 配置正确

### Q: 如何更新部署

**A:** 只需将代码推送到 GitHub 仓库，EdgeOne Pages 会自动检测到变化并触发重新部署。

## 🎯 部署最佳实践

1. **使用环境变量**：敏感信息（如 API 密钥）应通过环境变量配置，而不是硬编码在代码中
2. **优化构建**：确保项目构建产物最小化，提高加载速度
3. **定期更新**：及时更新依赖包，修复安全漏洞
4. **监控部署**：定期检查网站状态，确保服务正常运行

## 📞 支持

如果您在部署过程中遇到问题，可以：

1. 查看 [EdgeOne Pages 文档](https://www.tencentcloud.com/document/product/1145/70404?lang=zh)
2. 参考 [Next.js 部署文档](https://nextjs.org/docs/deployment)
3. 在 GitHub 仓库中提交 Issue

---

## 🤝 贡献

如果您有更好的部署方案或发现文档中的问题，欢迎提交 Pull Request 或 Issue。

---

> 🎉 祝您部署顺利！
