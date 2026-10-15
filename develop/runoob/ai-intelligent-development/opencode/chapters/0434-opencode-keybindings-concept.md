# OpenCode：OpenCode 快捷键配置详解

- 来源：[OpenCode 快捷键](https://www.runoob.com/opencode/opencode-keybindings.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：概念卡
- 章节序号：0434

## 本章内容

OpenCode 提供了一套完整的键盘快捷键系统，涵盖应用控制、会话管理、消息浏览、模型切换和输入编辑等各类操作。

所有快捷键均可通过 tui.json 文件进行自定义。


## 配置文件

快捷键配置写在 tui.json 文件的 keybinds 字段下，每条记录的键名为操作名称，值为对应的快捷键：


## 实例

一个操作可以绑定多个快捷键，用英文逗号分隔，任意一个触发即可执行该操作：


## 实例


## 前导键（Leader Key）

OpenCode 的大多数快捷键采用前导键（Leader Key）机制：先按下前导键，再按功能键，两键组合触发对应操作。这样设计的好处是避免与终端本身的快捷键产生冲突。

默认前导键为 ctrl+x。例如，新建会话的快捷键是 <leader>n，实际操作为：先按 ctrl+x，再按 n。

你可以将前导键改为任意组合键：


## 实例

不一定必须使用前导键机制来设置快捷键——也可以直接绑定普通按键或组合键。但建议优先使用前导键，以避免与终端快捷键冲突。


## 禁用快捷键

将任意快捷键的值设为 "none" 即可禁用该操作，禁用后按任何键都不会触发它：


## 实例


## 完整快捷键列表


### 1、应用与界面


### 2、会话管理


### 3、消息浏览


### 4、模型与代理


### 5、输入框编辑


### 6、文本选择


### 7、输入历史


## 桌面版内置输入快捷键

OpenCode 桌面版的提示词输入框额外内置了一套 Readline / Emacs 风格的文本编辑快捷键，这些快捷键为内置功能，无法通过 tui.json 修改或禁用：


## 配置 Shift+Enter 换行

部分终端默认不会将带修饰键的 Enter（如 Shift+Enter）作为独立按键发送，导致在 OpenCode 中按 Shift+Enter 无法换行而是直接发送消息。需要在终端中手动配置该按键的转义序列。


### Windows Terminal 配置方法

第一步：打开 Windows Terminal 的 settings.json 文件，路径为：

```text
%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json
```

第二步：在文件的根级 actions 数组中添加以下配置，定义一个发送 Shift+Enter 转义序列的动作：


## 实例

第三步：在文件的根级 keybindings 数组中添加按键绑定，将 Shift+Enter 映射到上面定义的动作：


## 实例

第四步：保存 settings.json 文件后，重启 Windows Terminal 或打开一个新标签页使配置生效。

如果你使用的是其他终端（如 iTerm2、Kitty、Alacritty 等），请参考对应终端的文档，找到"按键映射"或"Key bindings"相关设置，将 Shift+Enter 配置为发送 \u001b[13;2u 转义序列即可。


## 记忆卡片

- 一句话定义：`OpenCode 快捷键` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
