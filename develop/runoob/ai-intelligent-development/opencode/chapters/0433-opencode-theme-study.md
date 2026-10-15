# OpenCode：OpenCode 主题

- 来源：[OpenCode 主题](https://www.runoob.com/opencode/opencode-theme.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：学习笔记
- 章节序号：0433

## 本章内容

OpenCode 支持多种主题系统，您可以选择内置主题、自动适配终端主题，或者完全自定义主题，从而获得一致且舒适的终端体验。

最简单的方式就是在 TUI 输入框中输入 /themes 命令：

```text
/themes
```

然后在弹出的窗口中选择你喜欢的主题：


## 终端要求

为了确保主题能够正确显示完整色彩，您的终端必须支持 真彩色（24 位色）。

- 检查支持情况：

```text
echo $COLORTERM
```

输出应为：

```text
truecolor
或
24bit
```

- 启用真彩色：

```text
export COLORTERM=truecolor
```

- 常见支持终端：
- iTerm2
- Alacritty
- Kitty
- Windows Terminal
- GNOME Terminal（新版本）

如果终端不支持真彩色，主题将回退为 256 色，可能导致颜色失真。


## 内置主题

OpenCode 内置多种主题，可直接使用：


## system 主题（推荐）

system 主题会自动适配您的终端配色：

- 根据终端背景生成灰度层级
- 使用 ANSI 标准颜色
- 保持终端默认文本与背景

适用于：

- 使用自定义终端主题的用户
- 希望所有终端工具风格统一的用户


## 使用主题

方式一：在 TUI 中选择主题

```text
/themes
```

方式二：通过配置文件设置

tui.json

```text
{
  "$schema": "https://opencode.ai/tui.json",
  "theme": "tokyonight"
}
```


## 自定义主题

OpenCode 支持通过 JSON 定义完全自定义主题。


### 主题加载优先级

- 内置主题
- 用户目录：~/.config/opencode/themes/
- 项目目录：.opencode/themes/
- 当前目录：./.opencode/themes/

后加载的主题会覆盖前面的。


## 创建主题

用户级主题：

```text
mkdir -p ~/.config/opencode/themes
vim ~/.config/opencode/themes/my-theme.json
```

项目级主题：

```text
mkdir -p .opencode/themes
vim .opencode/themes/my-theme.json
```


## 主题格式说明

支持以下格式：

- 十六进制颜色：#ffffff
- ANSI 颜色：0-255
- 颜色引用：primary
- 深浅模式：

```text
{
  "dark": "#000000",
  "light": "#ffffff"
}
```

- 继承终端默认：

```text
"text": "none"
```


## 完整示例

my-theme.json

```text
{
  "$schema": "https://opencode.ai/theme.json",
  "defs": {
    "bg": "#1e1e2e",
    "fg": "#cdd6f4",
    "primary": "#89b4fa",
    "accent": "#f38ba8",
    "success": "#a6e3a1",
    "warning": "#f9e2af"
  },
  "theme": {
    "primary": {
      "dark": "primary",
      "light": "#005f87"
    },
    "accent": {
      "dark": "accent",
      "light": "#d7005f"
    },
    "background": {
      "dark": "bg",
      "light": "#ffffff"
    },
    "text": {
      "dark": "fg",
      "light": "#000000"
    },
    "border": {
      "dark": "#313244",
      "light": "#cccccc"
    },
    "syntaxKeyword": {
      "dark": "primary",
      "light": "#0000ff"
    },
    "syntaxString": {
      "dark": "success",
      "light": "#008000"
    },
    "syntaxComment": {
      "dark": "#6c7086",
      "light": "#999999"
    }
  }
}
```


## 总结

OpenCode 主题系统具备以下特点：

- 支持内置主题，开箱即用
- 支持 system 自动适配终端
- 支持 JSON 自定义主题
- 支持多层级覆盖机制

如果你追求极致体验，建议：

- 终端开启 truecolor
- 优先使用 system 主题或自定义主题


## 复习重点

- 能说明 `OpenCode 主题` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
