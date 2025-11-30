# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

Learn more about IDE Support for Vue in the [Vue Docs Scaling up Guide](https://vuejs.org/guide/scaling-up/tooling.html#ide-support).

## 部署到 Vercel

如果你想把这个静态站点快速发布到 Vercel（通过一个公网地址访问），有两种常用方式：通过 Vercel 仪表板或使用 Vercel CLI。

1. 通过 Vercel 仪表板（推荐）

   - 登录 https://vercel.com ，选择 "Import Project"，连接你的代码仓库（GitHub/GitLab/Bitbucket）。
   - Vercel 会自动检测 `package.json` 和构建命令；若没有识别，可手动设置：
     - Build Command: `npm run build`
     - Output Directory: `dist`
   - 点击部署，几秒钟后你会获得一个可访问的域名。

2. 使用 Vercel CLI（可在本地快速部署）

   - 安装并登录：

```bash
npm i -g vercel
vercel login
```

    - 在项目根目录运行部署：

```bash
vercel --prod
```

    - 或者用指定的构建命令（如果需要）：

```bash
vercel --prod --build-command "npm run build"
```

本仓库已包含 `vercel.json`（指定使用 `@vercel/static-build` 且输出目录为 `dist`），以及 `.vercelignore` 以减少上传文件。要在本地验证构建是否正确，请运行：

```bash
npm run build
# 然后检查是否生成了 dist/ 目录
```

如果你希望我帮助你把仓库连接到 Vercel 或生成 CI 自动部署设置（例如为主分支开启自动部署），告诉我你的代码托管平台（GitHub/GitLab/Bitbucket）和是否愿意授权我生成示例的 Vercel 仪表板步骤说明，我可以继续。
