# DeepSeek Harness：DeepSeek Harness 组合包 bundle 与 profile：两个 manifest

- 来源：[DeepSeek Harness 组合包](https://www.runoob.com/deepseek-harness/deepseek-harness-bundle-profile.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0238

## 本章内容

之前的章节我们用 --patch overlay 加载本地插件，这篇开始把它们打包成可安装的组合包。

本章节我们将讲清楚两个最基础的概念：bundle（组合包） 与 profile，以及它们各自的 manifest。


## 两个概念，两种 manifest

安装机制建立在两个概念之上，二者都由一份 package.json 描述。

它们在 dsh 键下携带的 manifest 种类不同，回答的问题也不同。

组合包是附带一个配置层的 npm 包。

它的 manifest 声明 dsh.bundle，回答的是"这个包贡献什么"：一个插入或覆盖插件行的 patch 文件。

profile 是位于 $DSH_HOME/profiles/<name> 下、描述一份可启动组合的目录。

它的 manifest 声明 dsh.profile，回答的是"这套配置由哪些组合包按什么顺序组成"。

bundle 是你编写并分发的东西；profile 是用户用 dsh --profile <name> 启动的东西。

没有东西同时是两者。

profile 位于安装目录之外，路径模板是 $DSH_HOME/profiles/<name>。


## 动手：创建 hello-plugin 组合包

按官方教程，先创建包目录。


## 实例

```text
mkdir -p hello-plugin
```

组合包目录结构如下，一共三个文件。


## 实例

```text
hello-plugin/
├── package.json       # 声明 dsh.bundle
├── cordis.patch.yml   # profile 列出该 bundle 时应用的配置层
└── index.js           # patch 行引用的插件模块
```

创建 hello-plugin/package.json，声明组合包 manifest。


## 实例

package.json 各字段的含义如下。

创建 hello-plugin/index.js，写入插件入口。


## 实例

创建 hello-plugin/cordis.patch.yml。


## 实例

这个 patch 与 --patch overlay 完全同构。

关键区别在 name 字段：这里写的是包名 dsh-hello-plugin，而不是相对源码路径。

安装后 pnpm 把包链接到 node_modules，Node 的模块解析就能按包名找到已安装的代码。

没有 dsh.bundle 声明的包仍然可以安装，但只作为普通依赖。

此时 dsh plugin 会打印警告，且不激活任何层。

如果一个库供插件包 import、而不是供用户启用，就使用这种包格式。


## profile manifest：从不需要手写

profile 目录包含两个文件。

第一个是 package.json，包含 profile 的树外插件依赖（由 pnpm 管理），加上 dsh.profile manifest 及其有序的 bundles 列表。

第二个是 cordis.patch.yml，是用户自己的 patch 层，在每个组合包层之后应用。

profile manifest 从不需要手写。

dsh plugin 负责创建和维护它，下一篇安装插件时会展示它的真实结果。


## 进阶：让表层组合包持有自己的命令行

定义了可运行应用的组合包，可以挂载一个普通提供方插件来持有自己的命令行。

这个提供方插件导出 inject = ['cmdlineArgs']，用自己的 commander program 调用 parseCmdline，再在 program 自己的 action 中把应用自有服务提供出去。


## 实例

受这些参数配置的行会注入提供方服务，并在自己的 !!js 选项中读取它，同时把部署取值写在旁边作为回退。


## 实例

启动器把自身 flag 之后的同一份不可变参数交给每个插件，因此添加应用专属 flag 无需修改启动器，多个插件也可以解析同一份快照。

遇到 --help 时，提供方不会发布该服务，所以这些行不会激活。

Loader 只挂载一次组合，等待每一行的普通注入，再基于其已注入的上下文求值该行的 !!js 配置。


## 小结与自测

组合包声明 dsh.bundle 回答"贡献什么"，profile 声明 dsh.profile 回答"由哪些 bundle 组成"，两者由一份 package.json 承载但 manifest 不同。

自测题：

- bundle 的 manifest 声明哪个键，回答什么问题？
- profile 位于哪个目录，它的 manifest 回答什么问题？
- 为什么 hello-plugin 的 cordis.patch.yml 里用包名而不是相对源码路径？


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 组合包` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
