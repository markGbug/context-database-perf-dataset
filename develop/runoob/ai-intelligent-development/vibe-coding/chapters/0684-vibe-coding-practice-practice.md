# Vibe Coding：Vibe Coding 实战项目

- 来源：[Vibe Coding 实战项目](https://www.runoob.com/vibe-coding/vibe-coding-practice.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：练习笔记
- 章节序号：0684

## 本章内容

本章节我们将完整演示 Vibe Coding 的全过程——不是埋头写代码，而是用自然语言描述需求、让 AI 来执行。

最终目标就是不写一行代码，也能做出一个真实可用的 Web 应用。


## 先搞懂：Vibe Coding 到底是什么

Vibe Coding 这个名字来自 OpenAI 联合创始人 Andrej Karpathy 的一条推文。

他的意思是：你沉浸在产品的「氛围」里，忘记代码细节，只描述你想要什么，AI 帮你实现。


### 和你现在的编程方式有什么区别


### Vibe Coding 的核心工作节奏

整个开发过程遵循一个简单的三步循环：

每完成一步就验证一步，通过之后再进入下一个循环。

这就是 Vibe Coding 的核心秘诀——不是一次性把所有需求丢给 AI，而是一小步一小步地推进，每步都确认方向正确。


## 环境准备

只需要三个东西，而且全部免费。


### 1. VS Code 编辑器

下载地址：https://code.visualstudio.com

VS Code 支持 Windows / macOS / Linux，完全免费。


### 2. GitHub Copilot（VS Code 已内置，无需安装）

VS Code 最新版本已经内置了 GitHub Copilot，不需要安装任何扩展。

我们只需要做一件事：

- 打开 VS Code，点击右上角的 账户图标
- 选择 Sign in with GitHub，登录你的 GitHub 账号
- 登录后 Copilot 自动激活

如果没有 GitHub 账号，先去 github.com 免费注册一个。

打开编辑器就能看到 Copilot 入口，只需要登录 GitHub 账号即可，无需去扩展市场安装插件。

点击右上角的小图标就可以调出 Copilot 聊天窗口：


### 3. Node.js

下载地址：https://nodejs.org

Node.js 教程：https://www.runoob.com/nodejs/nodejs-tutorial.html

选择 LTS 版本，安装后打开终端验证：

```text
node -v   # 应显示 v20.x.x 或更高
npm -v    # 应显示 10.x.x 或更高
```


### 认识几个快捷键

这两个快捷键是你最常用的：


## 项目立项：我们要做什么

现在我们要用 Vibe Coding 方式构建一个完整的任务管理应用。


### 功能清单

- 创建、编辑、删除任务
- 任务有三种状态：待办、进行中、完成
- 优先级分三档：高（红色）、中（黄色）、低（绿色）
- 看板视图：三列拖拽改变任务状态
- 深色模式：一键切换
- 数据自动保存到浏览器（刷新不丢失）
- 手机也能用（响应式布局）


### 技术选型


## 第一轮对话：搭骨架

现在我们开始真正的 Vibe Coding，不是一次性告诉 AI 所有需求，而是一步一步来。


### Step 1：创建项目

打开终端，创建项目：

```text
npm create vite@latest vibe-coding-runoob -- --template vue
```

打开新终端，进入该项目，然后按照 tailwindcss，使用 code . 命令让项目在 VS Code 中打开：

```text
cd vibe-coding-runoob
npm install
npm install -D tailwindcss @tailwindcss/vite
code .
```

现在 VS Code 打开了项目，按 Ctrl+Shift+I（Mac: Cmd+Shift+I）打开 Copilot Chat 面板，右上角也有个切换面板的按钮：


### Step 2：第一次对话

在 Chat 面板里输入下面这段话，就是把你想要的东西用自然语言说出来：

```text
我在开发一个任务管理 Web App，项目名 vibe-coding-runoob。
技术栈：Vue 3 + Vite + Tailwind CSS。

请帮我搭建项目骨架，创建以下文件：

1. src/types/task.ts — 定义 Task 类型
   字段：id, title, description, status, priority, dueDate, createdAt
   status 可选值：'todo' | 'in-progress' | 'done'
   priority 可选值：'low' | 'medium' | 'high'

2. src/App.vue — 应用主页面
   - 顶部导航栏（标题"Vibe Coding Runoob"）
   - 中间显示任务列表区域

要求：
- 使用 Vue 3 script setup 语法
- 使用 Tailwind CSS 做样式
- 界面简洁干净，主色调用 indigo（靛蓝色）
- 现在先用假数据展示，后面再接真实功能
```

AI 会一段一段地输出代码并修改文件代码，你点击 保留 让它自动写入文件。

申请执行命令，你只需要点允许就可以了：


### Step 3：验证

AI 代码写完后，会提示我们可以在终端运行：

```text
npm run dev
```

右上角点击打开终端按钮，然后在终端执行命令：

浏览器打开 http://localhost:5173，看到页面就说明第一步成功了。

完成效果如下：

这就是 Plan → Execute → Verify 的第一轮。你描述了目标，AI 执行了，你验证了结果。后面的每一轮都按这个节奏来。


### 遇到不懂的代码？

Vibe Coding 不需要你读懂每一行代码。但如果某段代码你完全看不懂，选中它，按 Ctrl+I，输入：

```text
用通俗的中文解释这段代码在做什么
```

AI 会用你能理解的语言解释它。


## 第二轮对话：实现任务列表和表单

骨架跑通了，现在来实现真正的功能。


### Step 1：任务卡片组件

继续在 Chat 面板输入：

```text
创建 src/components/TaskCard.vue 组件：

功能：
- 展示单个任务的信息：标题、描述、优先级标签、截止日期
- 优先级用颜色区分：high 红色、medium 黄色、low 绿色（左边框即可）
- 点击左侧复选框标记任务为完成（标题加删除线）
- 右上角有删除按钮（× 图标）
- 鼠标悬停时卡片微微放大（hover:scale-[1.02]）

Props 接收：task（Task 类型）
Emit 事件：toggle（切换完成状态）、delete（删除任务）
```

AI 生成后文件写入点保留，命令执行点允许，最后效果：

然后创建任务列表容器：

```text
创建 src/components/TaskList.vue 组件：

功能：
- 接收任务列表，用 TaskCard 展示每一项
- 任务按创建时间倒序排列（最新的在上面）
- 顶部有状态筛选按钮：全部 / 待办 / 进行中 / 完成
- 没有任务时显示空状态提示："还没有任务，点击下方按钮创建第一个吧"
```


### Step 2：创建任务表单

```text
创建 src/components/TaskModal.vue 组件：

功能：
- 点击"+ 新建任务"按钮打开弹窗
- 表单字段：标题（必填）、描述（选填）、优先级（下拉选择）
- 标题为空时显示红色错误提示"标题不能为空"
- 点击弹窗外的灰色遮罩关闭弹窗
- 按 ESC 键关闭弹窗
- 提交后用 emit 把新任务传给父组件

使用 v-model 绑定表单数据
使用 Teleport 把弹窗渲染到 body 下
```


### Step 3：把组件拼起来

现在更新 App.vue，把 TaskList 和 TaskModal 组合到一起：

```text
更新 src/App.vue：

- 引入 TaskList 和 TaskModal 组件
- 使用 reactive 管理 tasks 数组（先用示例数据）
- 实现 addTask 函数：接收 TaskModal 提交的数据，添加到 tasks 数组
- 实现 toggleTask 和 deleteTask 函数
- TaskModal 的显示/隐藏用 ref(false) 控制

示例数据包含 2 条任务，让页面看起来不空
```


### Step 4：验证

在浏览器里手动操作一遍：新建任务 → 点复选框标记完成 → 删除任务。全部功能正常运转后，进入下一轮。


## 第三轮对话：数据持久化

现在刷新页面任务就没了。我们需要把数据存到浏览器的 localStorage 里。


### 告诉 AI 你的需求

```text
现在任务数据只存在内存里，刷新就没了。请把数据持久化到 localStorage：

1. 创建 src/utils/storage.ts：
   - saveTasks(tasks): 把任务数组存为 JSON
   - loadTasks(): 读取并解析 JSON，读取出错时返回空数组
   - 存储键名：vibe-coding-runoob-tasks

2. 更新 src/stores/taskStore.ts：
   - 用 Vue reactive 管理状态
   - 初始化时从 localStorage 加载数据
   - 使用 watch 自动监听变化并保存（deep: true）
   - 导出 addTask、updateTask、deleteTask 函数
   - 首次使用时如果没有数据，自动创建 3 条示例任务

3. 更新 App.vue，改为从 taskStore 获取数据和方法
```


### 验证

```text
# 在浏览器中：
1. 添加几条任务
2. 刷新页面 → 任务还在！
3. 按 F12 打开开发者工具 → Application → Local Storage
4. 找到 vibe-coding-runoob-tasks，查看存储的 JSON 数据
```

如果数据没了，把 F12 控制台里的错误信息粘贴给 AI，让它修复。


## 后续章节

- 第四轮对话：看板视图
- 需求描述
- 第五轮对话：深色模式和移动端适配
- 深色模式
- 移动端适配
- 遇到 Bug 怎么办：万能排错模板
- 让 AI 审查你的代码
- 部署上线
- 推送到 GitHub
- 部署到 Vercel
- Vibe Coding 总结
- 写好提示词的公式
- 迭代节奏
- 这些事不要丢给 AI

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vibe Coding 实战项目` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
