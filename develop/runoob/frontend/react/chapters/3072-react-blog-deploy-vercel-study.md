# React：打包上线 — 部署到 Vercel

- 来源：[打包上线](https://www.runoob.com/react/react-blog-deploy-vercel.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3072

## 本章内容

本章你将学会如何把本地开发的博客项目打包，并免费部署到互联网上，获得公开的访问链接。


## 构建生产包

开发时运行 npm run dev，Vite 在本地启动开发服务器，支持热更新。

部署时需要的是优化压缩后的生产包。

```text
$ npm run build
```

执行后，项目根目录下生成 dist/ 文件夹：

```text
dist/
├── index.html                # 入口 HTML
├── assets/
│   ├── index-Df3aBc9x.js    # 打包压缩后的 JS
│   ├── index-Gh7jKl2m.css   # 提取并压缩后的 CSS
│   └── ...
├── posts.json                # public 目录文件原样复制
└── favicon.svg               # 静态资源
```

关键变化：

- 文件名带 hash（内容变了 hash 就变，用于浏览器缓存控制）
- 代码已压缩和 Tree-shaking（移除未使用的代码）
- public/ 目录内容原样复制到根目录

预览构建结果：运行 npx vite preview，在本地用生产模式启动服务，模拟线上环境。


## 将项目推送到 GitHub


### 第一步：创建 GitHub 仓库

在 GitHub 点击 + → New repository，填写：

- Repository name：react-blog-app
- 设为 Public（免费部署）
- 不勾选 Initialize with README


### 第二步：初始化 Git 并推送

```text
$ cd blog-app
$ git init
$ git add .
$ git commit -m "初始化 React 博客项目"
$ git branch -M main
$ git remote add origin https://github.com/你的用户名/react-blog-app.git
$ git push -u origin main
```

推送前确认 .gitignore 包含 node_modules 和 dist。node_modules 不应上传（能通过 npm install 恢复），dist 由构建平台自动生成。


## Vercel 部署

Vercel 是目前最流行的前端部署平台，对 React/Vite 项目零配置支持。


### 部署步骤

- 访问 vercel.com，用 GitHub 账号登录
- 点击 "New Project" → Import Git Repository → 选择 react-blog-app
- Vercel 自动识别 Vite + React，配置自动填充
- 点击 "Deploy"，等待几十秒
- 部署成功后，获得链接如：https://react-blog-app.vercel.app


### 自动部署

此后每次 git push，Vercel 自动：拉取代码 → npm install → npm run build → 部署上线。

整个过程全自动，推送即上线。


## 自定义域名（可选）

- Vercel 项目 Dashboard → Settings → Domains
- 输入你的域名（如 blog.runoob.com）
- 在 DNS 服务商处添加 CNAME 记录指向 cname.vercel-dns.com
- 等待 DNS 生效，Vercel 自动申请 SSL 证书


## 下一步学习方向


### React vs Vue3 全栈路线对照

最重要的一步你已完成——用 React 完整地做出一个真实项目。后续无论是 TypeScript 还是 Next.js，都是在已有基础上叠加维度。React 的思维方式（状态驱动视图、组件化、单向数据流）会在你的每个后续项目中发挥作用。


## 复习重点

- 能说明 `打包上线` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
