# Pi Agent：Pi Agent 扩展入门

- 来源：[Pi Agent 扩展入门](https://www.runoob.com/pi-agent/pi-agent-extensions-intro.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0493

## 本章内容

Extensions（扩展）是 Pi Agent 最强大的定制方式——你可以用 TypeScript 编写自定义工具、命令和事件监听器。


## 什么是 Extension

Extension 是一个 TypeScript 模块，它可以做下面这些事。


## 第一个 Extension：Hello World

下面这个扩展一次性演示了事件监听、工具注册和命令注册三种能力。


## 实例

第 13 行的事件判断用了最简单的 event.toolName 写法，也可以用类型守卫把 event 收窄成具体事件类型，见《事件系统》一章。

用 pi -e 参数启动 Pi Agent，即可加载这个扩展进行测试：

```text
$ pi -e ~/.pi/agent/extensions/my-extension.ts
Loading extension: /Users/runoob/.pi/agent/extensions/my-extension.ts
my-extension 加载成功（1 个工具、1 个命令）
我的扩展已加载！
```

最后一行就是 session_start 事件里 ctx.ui.notify 弹出的通知，说明扩展已经生效。


## 扩展的加载位置

Pi Agent 会在固定的几个目录中自动发现扩展，也可以显式指定路径。

除了命令行参数，也可以在 settings.json 的 extensions 字段中写入路径数组，目录路径会按扩展目录规则展开。


## 实例

第一个元素是单文件扩展，第二个是目录扩展，实际使用时替换成你自己的扩展位置即可。


## Extension 文件结构

Extension 可以是单个 .ts 文件，也可以是一个带入口文件的目录。


### 单文件扩展

最简单的形式，适合小型扩展：

```text
~/.pi/agent/extensions/
└── my-extension.ts
```


### 目录扩展（含 index.ts）

适合多文件扩展：

```text
~/.pi/agent/extensions/
└── my-extension/
    ├── index.ts        # 入口文件（导出默认函数）
    ├── tools.ts        # 辅助模块
    └── utils.ts        # 工具函数
```


### 带依赖的扩展

适合需要 npm 包的大型扩展：

```text
~/.pi/agent/extensions/
└── my-extension/
    ├── package.json    # 声明依赖和入口
    ├── node_modules/   # npm install 后生成
    └── src/
        └── index.ts
```

扩展以你的系统权限运行，可以执行任意代码。

只安装来自可信来源的扩展。


## 扩展的加载机制

扩展通过 jiti 加载，TypeScript 代码无需编译即可直接运行。

如果你的工厂函数返回 Promise，Pi Agent 会在继续启动流程之前等待它完成。

这意味着你可以在扩展初始化时做异步操作，比如获取远程配置。


## 可用 Import 包

这些包由 Pi Agent 内置提供，扩展中可以直接 import。

这些内置核心包由 Pi 自身提供，列为 peerDependencies 即可，不要打包进你的扩展。

自有运行时依赖则必须写进 package.json 的 dependencies 字段。

Pi 安装扩展包时默认执行生产安装（npm install --omit=dev），devDependencies 在运行时不可用。

其他 npm 包也可以使用——在扩展目录中添加 package.json 并运行 npm install 即可。


## 开发提示

这几条经验能帮你少走弯路，尤其是加载方式的选择。


## 进一步集成

除了编写扩展，官方还提供两条编程接入路线。

Node 或 TypeScript 项目可以直接使用 @earendil-works/pi-coding-agent 导出的 SDK：用 createAgentSession 创建会话、subscribe 订阅事件、prompt 发送消息。

这种方式与 Pi 同进程运行，类型定义完整。

跨语言调用或需要进程隔离时，改用 pi --mode rpc，通过 JSONL 协议与 Pi 进程通信。

两条路线与扩展共用同一套事件模型，选哪条主要看你是否需要独立进程。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 扩展入门` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
