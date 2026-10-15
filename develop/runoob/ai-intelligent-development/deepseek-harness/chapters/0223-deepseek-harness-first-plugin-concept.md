# DeepSeek Harness：DeepSeek Harness 第一个插件

- 来源：[DeepSeek Harness 插件](https://www.runoob.com/deepseek-harness/deepseek-harness-first-plugin.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0223

## 本章内容

在 Harness 中，插件是一个导出 apply 函数的 TypeScript 模块。

框架在加载插件时调用 apply，并传入一个 ctx（上下文对象）。

我们通过 ctx 注册能力，比如事件监听、工具、LLM 适配器。

ctx（Context）是框架传给每个插件的上下文对象。

ctx 既是注册能力的入口，也记录了插件注册的一切资源。


## 创建本地项目

我们需要先通过源码安装：

```text
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

接下来创建一个 scratch-plugin 项目，用来放我们的插件。

在仓库根目录执行：

```text
mkdir -p scratch-plugin/src
```


## 最小插件：hello-plugin

在 scratch-plugin/src 下创建 my-plugin.ts。

```text
cd scratch-plugin/src
```

下面是完整可用的插件配置，不差任何东西。


## 实例

这段代码只做一件事：加载时打印一行日志，它没有注册任何能力，但已经是一个合格的插件。


## 插件的三种形态

除了上面看到的函数形式，插件还支持对象形式和类形式。


### 函数形式

把 name 和 apply 分开导出，是官方示例默认的写法。


## 实例


### 对象形式

把 name、inject 和 apply 放进一个默认导出的对象。


## 实例


### 类形式

类形式继承 Service 基类，适合对外提供服务的插件。


## 实例


## 怎么选

大多数情况下，函数形式就足够了。

当插件需要向其他插件提供服务时，用类形式。

提示：类形式的核心是 super(ctx, '服务名')。

服务与依赖的完整机制会在第 14 篇展开。


## 记忆卡片

- 一句话定义：`DeepSeek Harness 插件` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
