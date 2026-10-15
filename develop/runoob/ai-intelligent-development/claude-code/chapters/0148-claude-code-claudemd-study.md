# Claude Code：CLAUDE.md 使用指南

- 来源：[CLAUDE.md 使用指南](https://www.runoob.com/claude-code/claude-code-claudemd.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0148

## 本章内容

CLAUDE.md 是 Claude Code 中最重要的配置文件，用于向 Claude 传递项目级别的持久指令。每次启动 Claude Code 会话时，它都会自动读取并加载这个文件中的内容，作为系统级上下文融入每一次对话中。

通俗地说，CLAUDE.md 就是你在项目中给 Claude 写的一份工作手册——告诉它这个项目是什么、遵循什么规范、有哪些注意事项，让它每次都能以符合项目要求的方式工作，而不是每次对话都重新解释。


## CLAUDE.md 的作用

没有 CLAUDE.md 时，Claude 每次都从零开始理解你的项目，你需要反复告诉它：用哪个包管理器、代码风格是什么、测试怎么跑、哪些文件不要动……有了 CLAUDE.md，这些信息只需写一次，Claude 每次都会遵守。

具体来说，CLAUDE.md 可以帮你做到以下几件事：

- 统一团队行为：将文件提交到 git，所有团队成员使用 Claude Code 时都遵循相同的规范
- 减少重复沟通：项目约定、架构规则、禁止事项只写一次，永久生效
- 降低出错概率：明确告知 Claude 哪些操作有风险，避免它做出错误的决策
- 加速 AI 理解：帮助 Claude 快速定位关键文件和理解项目结构，减少不必要的文件探索


## 文件放置位置

Claude Code 会从多个位置加载 CLAUDE.md，不同位置的文件作用范围不同：

当多个位置都存在 CLAUDE.md 时，Claude Code 会将它们全部加载并合并，优先级从高到低依次为：

```text
项目本地 → 项目根目录 → 子目录 → 全局用户级
```

项目根目录的 CLAUDE.md 建议提交到 git，让整个团队共享同一套 AI 工作规范。

个人偏好（如不喜欢加分号）放在 .claude/CLAUDE.md 中并加入 .gitignore，不影响他人。


## 快速创建 CLAUDE.md

最简单的方式是让 Claude Code 自动生成初始版本。在项目目录中启动 Claude Code 后，执行：

```text
/init
```

Claude Code 会分析你的项目结构、代码风格、已有配置文件（如 package.json、pyproject.toml、.eslintrc 等），自动生成一份符合项目实际情况的 CLAUDE.md，然后你可以在此基础上补充和调整。

也可以在项目目录中手动创建：

```text
touch CLAUDE.md
```


## 文件内容结构

CLAUDE.md 是一个普通的 Markdown 文件，没有强制的格式要求，但良好的结构能帮助 Claude 更快找到关键信息。以下是推荐的内容结构：

```text
# 项目名称

一句话说明这个项目是什么，方便 Claude 快速定位项目性质。

## 技术栈
- 语言：Python 3.11
- 框架：FastAPI 0.110
- 数据库：PostgreSQL 15 + SQLAlchemy ORM
- 测试：pytest

## 常用命令

### 开发
```bash
uv run uvicorn main:app --reload   # 启动开发服务器
uv run pytest                       # 运行所有测试
uv run pytest -k "test_auth"        # 运行指定测试
```

### 代码检查
```bash
uv run ruff check .                 # 代码检查
uv run ruff format .                # 代码格式化
```

## 项目结构
- `src/api/` — API 路由和请求处理
- `src/models/` — 数据库模型定义
- `src/services/` — 业务逻辑层
- `tests/` — 测试文件，与 src/ 目录结构镜像对应

## 编码规范
- 使用 `uv` 管理依赖，不使用 pip 直接安装
- 所有函数必须有类型注解
- 字符串一律使用双引号
- 新增 API 路由必须同步添加测试

## 注意事项
- 不要修改 `migrations/` 目录下的已有文件，只能新增迁移文件
- `config/secrets.py` 包含敏感配置，禁止输出其内容到日志或终端
- 数据库操作必须通过 Service 层，不要在路由层直接操作 ORM
```


## 核心内容模块详解


### 1、常用命令

这是 CLAUDE.md 中最高频被参考的部分。Claude 在执行测试、构建、代码检查等任务时，会优先查找这里定义的命令，避免猜测或使用错误的命令：

```java
## 常用命令

### 安装依赖
```bash
npm ci                    # 安装依赖（CI 环境使用，严格按 lock 文件安装）
```

### 开发
```bash
npm run dev               # 启动开发服务器（端口 3000）
npm run build             # 构建生产版本
npm run preview           # 预览生产构建
```

### 测试
```bash
npm test                  # 运行所有测试
npm test -- --watch       # 监听模式
npm test -- --coverage    # 生成覆盖率报告
```

### 代码质量
```bash
npm run lint              # ESLint 检查
npm run lint:fix          # 自动修复可修复的问题
npm run typecheck         # TypeScript 类型检查
```
```


### 2、项目结构说明

帮助 Claude 快速定位文件，减少不必要的目录扫描，尤其在大型项目中效果明显：

```text
## 项目结构

```
src/
├── app/                  # Next.js App Router 页面
│   ├── (auth)/           # 需要登录才能访问的页面组
│   └── api/              # API 路由
├── components/           # 可复用 UI 组件
│   ├── ui/               # 基础 UI 组件（Button、Input 等）
│   └── features/         # 业务组件（按功能模块组织）
├── lib/                  # 工具函数和配置
│   ├── db/               # 数据库客户端和查询
│   └── auth/             # 认证相关逻辑
└── types/                # TypeScript 类型定义
```

关键文件：
- `src/lib/db/client.ts` — 数据库连接配置
- `src/middleware.ts` — 认证中间件，处理路由保护
- `env.example` — 所有必要的环境变量示例
```


### 3、编码规范

告知 Claude 项目的代码风格和约定，确保生成的代码与现有代码库风格一致：

```text
## 编码规范

### 通用
- 文件名使用 kebab-case（如 `user-profile.ts`），类名使用 PascalCase
- 优先使用具名导出（named export），避免默认导出（default export）
- 异步函数一律使用 async/await，禁止使用 .then() 链式调用

### 组件规范
- 组件文件与其测试文件放在同一目录（如 `Button.tsx` 和 `Button.test.tsx`）
- Props 类型使用 interface 定义，命名格式为 `${组件名}Props`
- 不要将业务逻辑写在组件中，提取为自定义 Hook 或 Service

### 错误处理
- API 路由使用统一的错误响应格式：`{ error: string, code: string }`
- 客户端错误通过 Error Boundary 捕获，不要在每个组件里单独 try/catch
```


### 4、架构约束与禁止事项

这是防止 Claude 犯"聪明但错误"决策的关键部分。对于你了解但 Claude 不知道的特殊情况，必须明确写出来：

```text
## 架构约束

- 所有数据库查询必须通过 `src/lib/db/queries/` 中的函数执行，不要在路由或组件中直接写 SQL
- 状态管理使用 Zustand，不要引入 Redux 或其他状态管理库
- 样式使用 Tailwind CSS utility class，不要新增 CSS 文件或使用 CSS Modules

## 注意事项（重要）

- `legacy/` 目录下的代码是遗留代码，**禁止修改**，只能读取
- `.env.local` 和 `.env.production` 包含真实密钥，**禁止输出文件内容**
- `prisma/migrations/` 中已有的迁移文件**禁止修改**，数据库变更只能新增迁移
- 修改 `src/middleware.ts` 前必须先告知我，该文件影响所有路由的认证逻辑
```


### 5、开发环境说明

帮助 Claude 理解项目的运行环境，避免因环境差异导致命令执行失败：

```text
## 开发环境

- Node.js：需要 v20 或以上版本（通过 `.nvmrc` 指定）
- 包管理器：pnpm（禁止使用 npm 或 yarn 安装依赖）
- 本地数据库：Docker Compose 启动（`docker compose up -d`）
- 端口：前端 3000，API 3001，数据库 5432

### 环境变量
参考 `.env.example` 文件配置本地环境变量，复制为 `.env.local` 后填入实际值。
必填项：`DATABASE_URL`、`NEXTAUTH_SECRET`、`NEXTAUTH_URL`
```


## 多模块仓库（Monorepo）的配置方式

在 Monorepo 中，可以在仓库根目录放一个全局 CLAUDE.md，每个子包目录下再放各自的 CLAUDE.md。Claude 打开某个子包的文件时，会同时加载根目录和该子包目录下的两个文件：

```text
my-monorepo/
├── CLAUDE.md                  ← 全局规范：共用命令、整体架构、通用约定
├── packages/
│   ├── web/
│   │   └── CLAUDE.md          ← 前端专属：React 规范、样式约定、构建流程
│   ├── api/
│   │   └── CLAUDE.md          ← 后端专属：API 设计规范、数据库约定
│   └── shared/
│       └── CLAUDE.md          ← 共享包：导出规则、版本管理约定
└── tools/
    └── CLAUDE.md              ← 工具脚本：特殊说明和使用限制
```

```text
<!-- 根目录 CLAUDE.md（全局规范） -->
# My Monorepo

使用 pnpm workspace 管理的前后端一体化项目。

## 全局命令
```bash
pnpm install          # 安装所有包的依赖
pnpm -r build         # 构建所有包
pnpm -r test          # 运行所有包的测试
pnpm --filter web dev # 只启动 web 包的开发服务器
```

## 包之间的依赖关系
- `web` 和 `api` 都依赖 `shared`
- 禁止 `shared` 依赖 `web` 或 `api`（防止循环依赖）
- 跨包引用使用包名（如 `@my-app/shared`），不要使用相对路径
```


## 用 @ 语法引用外部文件


## 复习重点

- 能说明 `CLAUDE.md 使用指南` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
