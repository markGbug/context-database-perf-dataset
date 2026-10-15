# OpenCode：OpenCode TUI（终端界面）

- 来源：[OpenCode TUI](https://www.runoob.com/opencode/opencode-tui.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0425

## 本章内容

OpenCode 提供了一个交互式终端界面（TUI，Terminal User Interface），用于在命令行中与 AI 进行高效协作开发。

TUI 是 OpenCode 的核心使用方式，所有代码分析、修改、执行都通过这个界面完成。

OpenCode TUI 本质是一个可执行命令的 AI 对话终端，它把开发、命令行和 AI 融合在一起。

所有的 TUI 命令使用斜杆 / 唤起。

在 TUI 输入框中输入 / 就会列出联想的命令：


### OpenCode TUI 命令

下面是对 OpenCode TUI 命令的表：


### TUI 核心交互补充（非斜杠命令）

OpenCode 的 TUI 本质是一个LLM + 项目上下文 + Git 状态管理 + 命令面板的复合交互层：

- / → 控制行为（类似 IDE 命令面板）
- @ → 注入上下文（文件级 RAG）
- ! → 执行环境操作（Shell 工具调用）
- ctrl+x → 高效快捷操作前缀


## 一、启动 TUI


### 1、在当前目录启动

```text
opencode
```

如果出现 EACCES: permission denied, open '' 是权限问题，我们可以修复目录权限：

```text
sudo chown -R $(whoami) ~/.local
```

然后执行：

```text
chmod -R 755 ~/.local
```

也可以暴力一点，直接用 sudo：

```text
sudo opencode
```

会自动加载当前项目作为工作目录：


### 2、指定项目目录启动

```text
opencode /path/to/project
```

适用于快速切换项目


## 二、基本交互

进入 TUI 后，你可以直接输入自然语言：

```text
帮我快速总结这个项目的结构
```

OpenCode 会结合项目代码给出分析结果:


## 三、文件引用（核心功能）

你可以使用 @ 来引用项目中的文件：

```text
这个项目的认证逻辑是如何实现的？查看 @packages/functions/src/api/index.ts
```

特点：

- 支持模糊搜索文件路径
- 自动读取文件内容
- 无需复制代码

非常适合阅读陌生代码


## 四、执行 Bash 命令

按下 ! 会切换到 shell 模式，该模式下的内容会作为 shell 命令执行：

```text
!
```

执行命令：

```text
ls -la
```

执行结果会自动加入对话上下文。

这样我们可以边问 AI，边执行系统命令。


## 五、斜杠命令（/ 命令）

输入 / 可以执行内置命令，例如：

```text
/help
```

打开帮助面板。


### 常用命令一览


## 六、快捷键（效率提升）

OpenCode 支持快捷键操作：

说明：

- Ctrl + X 是默认"前导键"
- 类似 Vim 的快捷键模式


## 七、编辑器集成（/editor）

你可以使用外部编辑器编写复杂提示：

```text
/editor
```

需要提前配置：

```text
export EDITOR="code --wait"
```

支持编辑器：

- VS Code（code）
- Cursor（cursor）
- Vim / Neovim
- Nano


## 八、会话管理


### 查看会话

```text
/sessions
```


### 新建会话

```text
/new
```

可以在多个任务之间切换


## 九、撤销与重做（重要）


### 撤销

```text
/undo
```

作用：

- 撤销消息
- 回滚代码修改


### 重做

```text
/redo
```

注意：

- 依赖 Git 管理代码变更
- 建议项目开启 Git


## 十、TUI 配置

可以通过配置文件自定义行为：

```text
opencode.json
```

示例：

```text
{
  "tui": {
    "scroll_speed": 3,
    "scroll_acceleration": {
      "enabled": true
    }
  }
}
```

说明：

- scroll_speed：滚动速度
- scroll_acceleration：平滑滚动（推荐开启）


## 十一、使用建议

- 多使用 @ 引用文件，提高准确率
- 复杂任务先用计划模式，使用 Tab 键切换模式。
- 小步迭代，不要一次做太复杂。
- 重要操作前确保 Git 已提交。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode TUI` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
