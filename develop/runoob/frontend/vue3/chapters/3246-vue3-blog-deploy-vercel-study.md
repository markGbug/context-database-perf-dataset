# Vue3：打包上线 — 部署到 Vercel

- 来源：[打包上线](https://www.runoob.com/vue3/vue3-blog-deploy-vercel.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3246

## 本章内容

本章你将学会如何把本地开发完成的博客项目打包，并免费部署到互联网上，获得一个公开的访问链接。


## 构建生产包

开发时运行 npm run dev，Vite 会在本地启动开发服务器，支持热更新。

但部署时需要的是优化过的小体积文件——这就是生产构建。

```text
$ npm run build
```

执行后，项目根目录下会生成一个 dist/ 文件夹：

```text
dist/
├── index.html                # 入口 HTML（资源引用已被替换为构建后的路径）
├── assets/
│   ├── index-Df3aBc9x.js    # 打包后的 JS（代码已压缩、tree-shaking）
│   ├── index-Gh7jKl2m.css   # 打包后的 CSS（已提取、压缩）
│   └── ...                   # 其他资源
├── posts.json                # public 目录的文件原样复制
└── favicon.ico               # 其他静态资源
```

注意几个关键变化：

- 文件名带有 hash（如 Df3aBc9x），内容变了 hash 就变，用于浏览器缓存控制
- 代码已被 压缩和 Tree-shaking（移除未使用的代码）
- JS 和 CSS 被拆分到独立的文件
- public/ 目录的内容原样复制到根目录

要预览构建结果，可以运行 npx vite preview，它会在本地用生产模式启动服务，模拟线上环境。


## 将项目推送到 GitHub

部署平台（如 Vercel）通常从 Git 仓库拉取代码并自动构建，所以需要先把项目上传到 GitHub。


### 第一步：创建 GitHub 仓库

在 GitHub 网站右上角点击 + 号 → New repository，填写：

- Repository name：blog-app
- 设为 Public（免费部署）
- 不勾选 Initialize this repository with a README（因为本地已有项目文件）


### 第二步：在本地初始化 Git 并推送

```text
$ cd blog-app
$ git init
$ git add .
$ git commit -m "初始化博客项目"
$ git branch -M main
$ git remote add origin https://github.com/你的用户名/blog-app.git
$ git push -u origin main
```

推送成功后，刷新 GitHub 页面，能看到所有项目文件。

推送前确认 .gitignore 文件已包含 node_modules 和 dist。node_modules 不应上传（它能通过 npm install 恢复），dist 应由构建平台自动生成。


## 在 Vercel 中部署

Vercel 是目前最流行的前端部署平台，对 Vue/Vite 项目支持零配置。


### 部署步骤

- 访问 vercel.com，用 GitHub 账号注册/登录
- 点击 "New Project" → Import Git Repository → 选择 blog-app 仓库
- Vercel 会自动识别项目是 Vite（Vue），无需任何配置
- 点击 "Deploy"，等待几十秒，构建完成
- 部署成功后，你会得到一个链接，如：https://blog-app.vercel.app


### 自动部署

此后每当你在本地修改代码并推送到 GitHub（git push），Vercel 会自动：

- 检测到仓库有新提交
- 拉取最新代码，执行 npm install
- 执行 npm run build 构建
- 部署到生产环境

整个过程无需任何操作，推送即上线。


## 自定义域名（可选）

Vercel 提供 .vercel.app 的免费子域名，你也可以绑定自己的域名。

- 在 Vercel 项目 Dashboard → Settings → Domains
- 输入你的域名（如 blog.runoob.com）
- 按提示在 DNS 服务商处添加 CNAME 记录指向 cname.vercel-dns.com
- 等待 DNS 生效（通常几分钟到几小时），Vercel 会自动申请 SSL 证书


## 下一步学习方向

你已经掌握了 Vue3 的核心技能，下面是根据不同目标的进阶路线：


## 复习重点

- 能说明 `打包上线` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
