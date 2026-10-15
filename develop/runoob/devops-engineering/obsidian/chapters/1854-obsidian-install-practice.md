# Obsidian：Obsidian 安装

- 来源：[Obsidian 安装](https://www.runoob.com/obsidian/obsidian-install.html)
- 分类：DevOps / 工程化
- 技术：Obsidian
- 笔记类型：练习笔记
- 章节序号：1854

## 本章内容

前往 obsidian.md 下载对应平台的安装包：

- macOS：下载 .dmg 文件，拖入 Applications 文件夹
- Windows：下载 .exe 安装程序，按引导安装
- Linux：提供 .AppImage、.deb、.rpm 三种格式
- iOS / Android：App Store / Google Play 搜索「Obsidian」

Obsidian 个人使用完全免费，无需注册账号即可使用所有核心功能。

你可以选择对应你的操作系统（Windows/Mac/iOS/Android/Linux）的版本下载并安装。

Obsidian 下载页面：https://obsidian.md/download

Obsidian Github 地址：https://github.com/obsidianmd

下载后就可以双击安装，选择语言等配置：


### 首次启动界面

首次打开 Obsidian 你会看到三个选项：

```text
创建新库         在本地新建一个 Vault
打开已有文件夹    将现有文件夹作为 Vault
从 Obsidian Sync 打开    （付费功能）
```

然后选择快速开始直接进入页面看看布局：

- 左侧栏 (文件管理器)： 管理你的文件夹和笔记列表。
- 中间区域 (编辑器)： 你主要写作的地方，支持"实时预览"模式，即你输入 Markdown 符号时，它会立刻渲染成格式。
- 右侧栏 (面板)： 默认显示反向链接（即其他哪些笔记提到了你正在看的这篇笔记）和大纲。
- 命令面板 (Ctrl/Cmd + P)： 新手神器！按此快捷键，输入你想要做的操作（如"创建新笔记"），无需点击菜单。

选择创建新库，为你的知识库起一个名字，选择一个存放位置。

建议放在 ~/Documents/ 下，便于备份和 Git 管理。


### 界面语言设置

Obsidian 默认显示英文界面。切换为中文的步骤：

- 打开设置：Cmd/Ctrl + ,
- 选择左侧 About（关于）
- 找到 Language 下拉菜单
- 选择「简体中文」
- 点击 Relaunch（重启）


### 认识三栏布局

重启后，你会看到 Obsidian 的主界面，由三个区域组成：

- 左侧边栏：文件列表、搜索、书签、标签列表
- 编辑区/阅读区：这是你写笔记的地方，支持编辑/预览双模式或分屏同时查看
- 右侧边栏：反向链接、大纲、标签等辅助面板


### 快捷键速查


### 推荐的初始外观配置

进入设置 → 外观，建议做以下调整：

主题：官方默认主题已经很好用。如果你喜欢更简洁的风格，可以在社区主题中搜索并安装 Minimal，它是目前最受欢迎的第三方主题之一。

字体设置（开发者推荐）：

- 界面字体：系统默认 或 PingFang SC（macOS）/ 微软雅黑（Windows）
- 正文字体：同上，或思源宋体用于阅读
- 等宽字体：JetBrains Mono 或 Fira Code（代码块使用）

进入设置 → 编辑器，建议调整：

- 行宽：建议设置为 88 或 100，与代码习惯保持一致
- 实时预览（Live Preview）：默认已开启，推荐保留
- 自动配对括号：开启，写 [[ 时自动补全 ]]
- 显示行号：可以开启，对开发者来说更亲切


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Obsidian 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
