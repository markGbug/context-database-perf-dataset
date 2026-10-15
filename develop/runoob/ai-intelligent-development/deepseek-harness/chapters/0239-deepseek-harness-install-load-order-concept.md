# DeepSeek Harness：DeepSeek Harness 安装插件与配置加载顺序

- 来源：[DeepSeek Harness 安装插件](https://www.runoob.com/deepseek-harness/deepseek-harness-install-load-order.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0239

## 本章内容

上一章节创建了 hello-plugin 组合包，这一篇把它安装进一个 profile。

安装步骤在 DeepSeek Harness 组合包 bundle 与 profile：两个 manifest 的基础上进行，可先回看那篇的两个 manifest。

本章节我们将同时回答一个关键问题：多个组合包的配置叠加时，到底谁覆盖谁。

这由生效配置的加载顺序决定。


## 加载顺序：生效配置的分层

生效配置在空根之上按固定顺序逐层组合，后应用的层按行胜出。

完整顺序如下。

应用参数不是另一层 patch。

表层组合包可以通过普通应用自有服务解析它们。

后应用的层按行胜出，且 patch 会替换目标行的整个 config 值，而不是深度合并各键。


## 动手：安装 hello-plugin 进 profile

dsh plugin --profile <name> <args...> 在 profile 目录内转发给 pnpm，因此所有 pnpm 子命令都可用。

在包含 hello-plugin 的目录中，安装该包的 checkout。

```text
dsh plugin --profile demo add ./hello-plugin
```

首次使用会初始化 profile。

@deepseek-ai/dsh-base 会成为它的第一个组合包。

pnpm 链接该 checkout，而 dsh 因为这个包声明了 dsh.bundle，把它追加进 dsh.profile.bundles。

生成的 profile 的 package.json 大致如下。


## 实例

各字段的含义如下。

先不启动、只验证该层，再启动。

```text
dsh --profile demo --dump-config   # 会显示一个 "# == dsh-hello-plugin" 层
dsh --profile demo
```

--dump-config 会把叠加后的生效配置打印出来，用于核对每一层来自哪个组合包。

输出里应能看到 # == dsh-hello-plugin 这样的层标记。

移除插件同样简单。

```text
dsh plugin --profile demo remove dsh-hello-plugin   # 同时移除依赖和对应的层
```


## patch 按 id 整行替换

patch 不是深度合并，而是按 id 整行替换目标行的整个 config 值。

这给组合包作者带来两个推论。

第一，你的 patch 可以按 id 覆盖前面各层的行。

就像 dsh-web-app 组合包覆盖 dsh-base 的行那样。

但必须重述该行需要的每一个键，而不是只写改动的那个。

第二，用户可以在自己 profile 的 cordis.patch.yml 中覆盖你的行，无需改动你的包。

所以优先给出用户大概率会保留的配置默认值，其余交给 schema 承担。

内置组合包名称始终从 dsh 安装目录本身解析。

pnpm 只管理树外的包，所以你的组合包可以放心依赖 @deepseek-ai/dsh-base 存在且与安装保持一致。


## 小结与自测

安装插件就是往 profile 的 bundles 列表追加一个声明了 dsh.bundle 的包，生效配置按 bundles → profile patch → home patch → --patch overlay 的顺序逐层叠加。

自测题：

- 生效配置的四层加载顺序是什么？
- patch 按 id 覆盖时，为什么必须重述所有键？
- dsh --profile demo --dump-config 的作用是什么？


## 记忆卡片

- 一句话定义：`DeepSeek Harness 安装插件` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
