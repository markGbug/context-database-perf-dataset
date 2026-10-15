# Pi Agent：Pi Agent 包管理

- 来源：[Pi Agent 包管理](https://www.runoob.com/pi-agent/pi-agent-packages.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0497

## 本章内容

Pi Packages(包) 允许你将 Extensions、Skills、提示词模板和主题打包，通过 npm 或 git 进行分发和安装。


## 包管理命令

所有包操作都通过 pi 命令完成，无需手动编辑 settings.json。

使用示例：

```text
# 安装 npm 包
$ pi install npm:@runoob/pi-todo-kit@1.0.0

# 安装 git 包
$ pi install git:github.com/runoob/pi-todo-kit@v1

# 安装本地包
$ pi install ./packages/pi-todo-kit
$ pi install ~/projects/pi-share-kit

# 安装为项目级（写入 .pi/settings.json）
$ pi install -l npm:@runoob/pi-todo-kit

# 临时试用包（不安装到配置中）
$ pi -e npm:@runoob/pi-todo-kit
$ pi -e git:github.com/runoob/pi-todo-kit
```

安装输出大致如下（示意），其中 extensions 和 skills 的数量取决于包的 pi 字段：

```text
$ pi install npm:@runoob/pi-todo-kit
Resolving @runoob/pi-todo-kit@1.2.0
Downloading @runoob/pi-todo-kit (12.4 kB)
Running npm install in ~/.pi/agent/npm/@runoob/pi-todo-kit
Installed @runoob/pi-todo-kit@1.2.0
  extensions: 2
  skills:     1
  prompts:    3
Saved to ~/.pi/agent/settings.json
```

上述包名与版本都是示意值，实际使用时替换成你要安装的包即可。


## 包来源

Pi Agent 支持三种包来源，安装行为和缓存位置各不相同。


### npm 包

npm 是推荐的包分发方式：

```text
pi install npm:@scope/pkg@1.2.3
pi install npm:pkg
```

带版本号的 npm 包会被锁定，pi update 不会自动升级它们。

包安装位置：全局在 ~/.pi/agent/npm/，项目级在 .pi/npm/。


### Git 包

支持 HTTPS 和 SSH 协议：

```text
# HTTPS
pi install https://github.com/user/repo@v1

# SSH（git@host:path 需要 git: 前缀）
pi install git:git@github.com:user/repo@v1

# SSH 协议
pi install ssh://git@github.com/user/repo@v1
```

Git 包的 ref 会被锁定，pi update 不会自动移动到新 ref。

克隆位置：全局在 ~/.pi/agent/git/，项目级在 .pi/git/。


### 本地路径

指向本地文件系统路径，不会复制文件：

```text
pi install /Users/runoob/.pi/agent/packages/my-kit
pi install ./packages/my-kit
```


## 创建 Pi 包

在 package.json 中添加 pi 字段：


## 实例

如果没有 pi 字段，Pi Agent 会自动从约定的目录中发现资源：

添加 pi-package 关键词可以让你的包出现在 Pi Agent 包画廊 中。

video 和 image 字段用于在画廊中展示预览。


## 包过滤

安装包时可以精确控制加载哪些资源，避免一次性带入全部内容。

下面的 packages 数组写入 ~/.pi/agent/settings.json（全局生效）或 .pi/settings.json（仅当前项目生效）。

用 pi install -l 安装的包就是写进了项目的 .pi/settings.json，两种方式最终都落在同一份配置里。

数组条目支持两种写法：字符串形式加载该包的全部资源，对象形式按资源类型逐项过滤。


## 实例

官方文档中 skills 过滤既有按包内路径的写法，也有按技能名的写法，实际以所装包的说明为准。

过滤规则如下：


## 依赖管理

Pi Agent 会为每个已安装的 npm/git 包执行 npm install，自动安装依赖。

随包分发的本地依赖可用 bundledDependencies 打包。

以下核心包由 Pi Agent 自身提供，应列为 peerDependencies，不要在包中重复打包：


## pi config 管理资源

使用 pi config 交互式地启用或禁用已安装包的扩展、Skills、模板和主题：

```text
# 编辑全局配置
$ pi config

# 编辑项目配置
$ pi config -l
```

Tab 键在全局和项目模式之间切换。


## 作用域与去重

同一个包可以同时出现在全局和项目配置中。

如果项目条目存在，它优先于全局条目。

例外是项目条目设置 autoload: false 时，不再整体覆盖，而是作为增量叠加到全局条目上。

包的身份由以下方式确定，Pi Agent 以此判断两条配置是否指向同一个包：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 包管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
