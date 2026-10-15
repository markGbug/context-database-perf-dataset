# Vue3：Vue3 目录结构

- 来源：[Vue3 目录结构](https://www.runoob.com/vue3/vue3-directory-structure.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3198

## 本章内容

上一章节中我们使用了 npm 安装项目(Vue-cli 和 Vite)，我们在 IDE（Vscode、Atom 等） 中打开该目录，结构如下所示：

命令行工具 vue-cli（runoob-vue3-test）：

Vite（runoob-vue3-test2）

一个标准的 Vue 3 项目，通常可以拆成三层：

- 项目根目录：构建工具与工程配置
- public 目录：不参与构建的静态资源
- src 目录：几乎所有业务代码都在这里，平时开发基本在这个目录里面。

典型的 Vue 项目结构：

```text
vue-project/
├── public/                  # 静态资源，直接复制到构建输出目录
│   └── favicon.ico          # 网站图标
├── src/
│   ├── assets/              # 静态资源（如图片、字体、CSS）
│   │   └── logo.png
│   ├── components/          # 可复用的通用组件
│   │   └── CommonHeader.vue
│   ├── composables/         # 可复用的 Composition API 逻辑（可选）
│   │   └── useFetch.js
│   ├── router/              # 路由配置
│   │   └── index.js
│   ├── stores/              # Pinia 状态管理（或 store/ 用于 Vuex）
│   │   └── index.js
│   ├── utils/               # 工具函数（如请求封装、格式化）
│   │   └── request.js
│   ├── views/               # 页面级组件（对应路由页面）
│   │   ├── HomeView.vue
│   │   └── AboutView.vue
│   ├── App.vue              # 根组件
│   └── main.js              # 入口文件（创建 Vue 应用）
├── index.html               # HTML 入口模板
├── vite.config.js           # Vite 配置文件
├── package.json             # 项目依赖与脚本
├── .gitignore               # Git 忽略文件
├── .env                     # 环境变量（开发）
├── .env.production          # 环境变量（生产）
└── README.md                # 项目说明
```


### 目录解析

随着项目变大，还可能需要添加这些文件夹：

- src/layouts/：不同页面布局（如 AdminLayout.vue、GuestLayout.vue）。
- src/plugins/：自定义 Vue 插件（如全局组件自动注册）。
- src/directives/：自定义指令（如 v-loading）。
- src/types/：全局 TypeScript 类型声明。
- tests/ 或 tests/：单元/E2E 测试（Vitest + Vue Test Utils）。
- src/api/：分离 API 接口调用模块（比 utils/request 更细粒度）。

接下来，我们以 runoob-vue3-test2 为例，打开目录下的 src/APP.vue 文件，代码如下（解释在注释中）：


## src/APP.vue 文件代码

接下来我们可以尝试修改下初始化的项目，将 src/APP.vue 修改为以下代码：


## src/APP.vue 文件代码

打开页面 http://localhost:3000/，一般修改后会自动刷新，显示效果如下所示:


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 目录结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
