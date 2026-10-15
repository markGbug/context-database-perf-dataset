# DeepSeek Harness：DeepSeek Harness 插件配置：Config 与 Schemastery

- 来源：[DeepSeek Harness 插件配置](https://www.runoob.com/deepseek-harness/deepseek-harness-plugin-config.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0228

## 本章内容

greet 工具把问候语写死在代码里，不同部署想换就得改代码。

本章节让插件接受 cordis.yml 传入的配置，做到"配置与代码分离"。


## 导出 Config 类型与同名 schema

在插件中导出一个 Config 接口和同名的 Schemastery schema。

默认值直接写在 schema 字段上。


## 实例

接口给 TypeScript 类型，schema 给运行时校验与默认值。

两者同名，是 Cordis 的约定。

不要导出普通对象作为 Config。

它不满足 Cordis 要求的 Standard Schema 接口。


## 在 cordis.yml 里传入配置

在新插入的本地插件行里加一个 config 字段。


## 实例

插件加载时，Cordis 会通过导出的 schema 校验配置，并填充未提供字段的默认值。

上面的配置里没写 verbose，它会取 schema 默认值 false。


## Schema 校验

需要更严格的校验时，用 Schemastery 表达约束。


## 实例

Schema 在插件加载时执行校验。

如果配置不合法，插件会加载失败，并给出明确错误信息。


## 设计原则：无硬编码可调参数

Harness 的约定是：凡是不同部署可能需要采用不同值的参数，都必须定义为配置字段。


## 错误与正确写法

检验标准一句话：能否在 cordis.yml 中改变这个值，而不需要修改代码？

如果能，就是合格的可调参数；如果不能，就要把它提成配置字段。

硬编码是把本应可调的值写死在代码里。

它让"改配置"变成"改代码加重新部署"，是生产事故的常见来源。


## 配置错误要响亮

在 schema 中表达自身完备的约束，让无效配置在插件加载时失败。

对服务或已注册资源的引用需要依赖注入，服务教程会介绍这项约定。


## 配合 HMR：配置热替换

配置变更会触发插件热替换（HMR）。

修改 cordis.yml 中某个插件的 config 后，框架会卸载旧实例并加载新实例。

由于注册都属于 effect 并会自动清理，替换后不会保留旧实例的注册。


## 小结与自测

导出 Config 接口与同名 schema，默认值写进 schema，配置在加载时校验；所有可调参数都进配置。

1. 为什么默认值写在 schema 而不是代码里？

2. 配置不合法时会发生什么？

3. 检验"无硬编码"的标准是什么？


## 复习重点

- 能说明 `DeepSeek Harness 插件配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
