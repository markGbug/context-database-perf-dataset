# DeepSeek Harness：DeepSeek Harness 服务与依赖：Service 基类与类型声明

- 来源：[DeepSeek Harness 服务与依赖](https://www.runoob.com/deepseek-harness/deepseek-harness-services.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0231

## 本章内容

前几个章节我们一直在用 ctx.tools、ctx.llm、ctx.agents 这些内置服务。

这一章节我们从服务提供方的视角出发，看如何用 Service 基类自己提供一个命名服务，并让消费方获得完整的类型提示。


## 什么是服务

在 Harness 中，tools、llm、agents 都是服务。

服务是挂载在 ctx 上的命名能力，任何插件都可以提供服务，供其他插件使用。

服务：一个插件向其他插件公开的能力。

它占据一个稳定的 ctx.<key>（如 ctx.tools、ctx.llm、ctx.sessions），其他插件通过 key 查找服务，而不是导入具体实现。

例如 ctx.tools 是工具运行时服务，ctx.llm 是大模型服务，ctx.agents 是智能体服务。

内置服务的服务名、公开方法和源码位置由仓库自动生成到各服务的子系统页面。开发插件时应以这些生成区块和服务的 TypeScript 接口为准，不要依赖任何手写的静态服务清单。


## 使用服务：inject 声明

使用已有服务，在插件里声明 inject。

框架保证：apply 执行时，inject 声明的服务已经全部就绪。


## 实例

如果服务还没准备好，你的插件会等着，不会执行 apply。


## 提供服务：Service 基类

用 Service 基类派生一个子类，在构造函数里调用 super(ctx, '服务名') 注册命名服务。


## 实例

加载这个插件后，消费方就能通过 ctx.metrics 访问它。


## 实例


## 类型声明：declare module 合并

使用 TypeScript 声明合并，让 ctx.metrics 拥有正确的类型。

这样写代码时会有自动补全，编译期也能发现拼错服务名的错误。


## 实例

declare module 声明合并是 TypeScript 给已有模块补类型的标准做法。

这里把 ctx.metrics 的类型与实现写在同一个文件里，保证两者不漂移。


## 必需依赖与可选依赖

服务依赖分为必需与可选两种。

必需依赖用 inject 声明，服务缺席时插件根本不加载。

可选依赖省略 inject，在使用处用 ctx.get() 查询，可能得到 undefined。


## 实例

什么时候用可选依赖？当服务可有可无、你的插件在它缺席时也要正常工作。


## 服务消失时的行为

如果应用运行期间某项必需服务消失（例如它的提供方被卸载），会发生两件事：

- 依赖它的插件会自动 dispose（释放资源）。
- 当服务重新出现时，插件自动重新加载。

这可以防止插件调用已不存在的服务。


## 小结自测

Service 子类通过 super(ctx, '名字') 提供命名服务，declare module 声明合并补齐类型，inject 声明必需依赖、ctx.get() 查询可选依赖。

自测一下：

- 服务在 ctx 上以什么形式存在？服务名由哪个参数决定？
- 如何让 ctx.metrics 有类型提示？
- 必需依赖与可选依赖的代码写法有什么不同？


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 服务与依赖` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
