# Pi Agent：Pi Agent 键盘快捷键定制

- 来源：[Pi Agent 键盘快捷键定制](https://www.runoob.com/pi-agent/pi-agent-keybindings.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：概念卡
- 章节序号：0487

## 本章内容

Pi Agent 的快捷键完全可定制。本章介绍默认快捷键配置以及如何创建自己的快捷键方案。


## 配置文件

快捷键配置文件位于 ~/.pi/agent/keybindings.json。

修改后执行 /reload 即可生效，无需重启。


## 快捷键格式

快捷键格式为 修饰键+按键，修饰键包括 ctrl、shift、alt、super，可以组合使用。

其中 super 需要终端能够单独上报该修饰键（通常依赖 Kitty 键盘协议）才会生效，不支持的终端里可能无效。

支持的按键分为以下几类：

配置文件中修饰键使用小写（例如 ctrl+shift+p），正文表格习惯写作 Shift+Ctrl+P，两者等价。


## 默认快捷键速查

以下四张表按功能区域列出出厂默认绑定，作为自定义时的对照基准。

本章仅列出常用绑定，ctrl+]、ctrl+alt+]、pageUp/pageDown、alt+y、ctrl+z 以及会话选择器按键等并未收录，完整列表可在交互模式中用 /hotkeys 查看。


### 编辑器操作

这一组只在编辑区生效，负责光标移动与文本删除。


### 输入与提交

这一组控制内容如何换行、补全和提交，同样作用于编辑区。


### 应用与消息

这一组负责打断 AI、管理编辑区内容和消息队列，多数不依赖编辑区焦点。


### 模型与推理

这一组用于切换模型和调整推理行为，在对话过程中随时可用。


## 自定义快捷键配置

在 keybindings.json 中列出想覆盖的操作即可，未列出的操作保持默认。

把某个绑定的值写成空数组，例如 "tui.altScreen.pageUp": []，可以彻底禁用该快捷键。


### Emacs 风格

如果你习惯 Emacs 的快捷键，可以在 ~/.pi/agent/keybindings.json 中使用以下配置：


## 实例

historyPrevious 和 historyNext 这两个历史记录动作默认没有绑定，专门用于翻阅提交历史，且在多行输入中也会切换历史条目。

把 ctrl+p 绑到历史上一条之后，编辑区获得焦点时 Ctrl+P 会被这条历史绑定抢占，模型向前切换在这个场景下暂时失效。

模型选择器等选择列表中的 Ctrl+P 不受影响，仍执行选择器自身的动作。


### Vim 风格

如果你习惯 Vim 的方向键，可以使用以下配置：


## 实例

这里选用 alt+h/j/k/l，是为了避开 Ctrl+H/Ctrl+D 等内置绑定，故用 Alt 系。

Pi Agent 的快捷键配置会覆盖默认值。

每个操作可以绑定一个或多个快捷键。

配置文件中未列出的操作保持默认快捷键不变。


## 查看所有快捷键

在交互模式中，使用以下命令显示所有快捷键及其当前绑定：

```text
/hotkeys
```

输出片段：

```text
编辑器
  tui.editor.cursorUp            up
  tui.editor.cursorDown          down
  tui.editor.cursorWordLeft      alt+left, ctrl+left, alt+b
  tui.input.submit               enter
模型与推理
  app.model.select               ctrl+l
  app.model.cycleForward         ctrl+p
  app.model.cycleBackward        shift+ctrl+p
```

快捷键操作使用带命名空间的 id，格式为「模块.动作」。

旧版本配置文件里没有命名空间的 id（如 cursorUp、expandTools）会在启动时自动迁移为命名空间 id，无需手动修改。

这个命令会列出所有可用的快捷键操作、当前绑定和所属的功能区域，是排查快捷键冲突或查找特定功能快捷键的最佳方式。


## 全屏模式下的按键

用 --tui-mode fullscreen 启动时，对话记录（transcript）在终端视口内滚动，编辑区与底部状态区域保持固定。

此时不带修饰键的 home、end、pageUp、pageDown 用于滚动对话记录，它们的 ctrl 变体仍归编辑器使用。

在常规模式下，这两组按键都作用于编辑器。

全屏模式还有专属的搜索与跳转：ctrl+shift+f 搜索对话记录，ctrl+up、ctrl+down 在上一条与下一条标记消息之间跳转。

全屏滚动绑定的优先级高于编辑器绑定，仍可通过普通动作绑定自行调整。


## 记忆卡片

- 一句话定义：`Pi Agent 键盘快捷键定制` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
