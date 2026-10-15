# Playwright：Playwright VS Code 开发环境配置

- 来源：[Playwright VS Code](https://www.runoob.com/playwright/playwright-setup.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0509

## 本章内容

Playwright 开发推荐用 VS Code，因为它对 JavaScript/TypeScript、调试器、扩展支持都很强大。


## 安装 VS Code

- 前往 VS Code 官网 下载并安装。
- 安装完成后，建议同时装上 中文语言包（扩展市场搜索 Chinese (Simplified)）。

VS Code 相关内容参考：https://www.runoob.com/vscode/vscode-tutorial.html


## 必备扩展插件

在 VS Code 的扩展（Extensions）面板里，搜索并安装以下插件：

Playwright Test for VSCode

- 官方出品的 Playwright 插件
- 功能：运行/调试用例、查看测试报告、录制脚本、生成 trace
- 扩展 ID：ms-playwright.playwright

JavaScript / TypeScript 支持（VS Code 自带，通常不用额外装）

推荐（可选）：

- ESLint（保证代码风格一致）
- Prettier - Code formatter（一键格式化代码）


## 初始化 Playwright 项目

如果还没初始化过项目，先执行：

```text
npm init playwright@lates
```

VS Code 插件会自动识别项目里的 playwright.config.ts/js，并启用测试视图。


## VS Code 设置

打开 VS Code 设置（快捷键 Ctrl+, 或 Cmd+,），确认以下配置：

- 保存时自动格式化 搜索 format on save → 勾选 Editor: Format On Save
- 终端默认 shell（根据自己系统选择） Windows 推荐 PowerShell 或 Git Bash macOS/Linux 默认即可


## 调试配置（launch.json）

在 VS Code 左侧点击 运行与调试 → 创建配置，选择 Node.js，生成 .vscode/launch.json，添加 Playwright 调试配置，例如：

```text
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Playwright Test",
      "type": "node",
      "request": "launch",
      "program": "${workspaceFolder}/node_modules/.bin/playwright",
      "args": ["test", "--project=chromium", "--headed"],
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}
```

这样就可以在 VS Code 里按 F5 启动调试，Playwright 会跑在有界面模式，方便观察。


## 使用 Playwright 插件面板

安装好 Playwright Test for VSCode 插件后，左侧会出现一个"Playwright"图标：

- 可以直接看到项目里的测试文件和用例列表
- 点击某个用例右侧的 ▶ 按钮就能运行
- 右键选择 Debug Test 可以单步调试
- 运行失败的测试可以直接查看 trace 文件


## 常用命令

在 VS Code 的终端运行：

```text
npx playwright test           # 运行全部测试
npx playwright test login.spec.js # 运行指定文件
npx playwright codegen        # 启动录制工具（自动生成脚本）
npx playwright show-report    # 打开测试报告
```


## Testing Sidebar 测试侧边栏

安装扩展后，VS Code 左侧会出现 Testing 图标（实验室烧杯图标）。

点击进入 Testing Sidebar，可以看到所有测试文件列表。

在这里你可以：

- 展开文件查看每个 describe 和 test
- 点击播放按钮运行单个测试或全部测试
- 实时查看测试执行状态（绿色通过、红色失败、灰色跳过）
- 右键测试访问更多选项（调试、跳转到定义等）


## Debug Mode 调试

VS Code 扩展让你可以像调试普通代码一样调试 Playwright 测试：


### 设置断点

在代码行号左侧点击即可添加红色断点。

右键点击断点旁边，选择 Debug Test，测试会在断点处暂停。


### 调试功能

- 单步跳过（F10）、单步进入（F11）、单步跳出（Shift+F11）
- 查看变量当前值
- 查看调用堆栈
- 在调试控制台中执行表达式


## Live Debugging 实时调试

Live Debugging 是 VS Code 扩展的独特功能。

启用 Show Browser 选项运行测试时，点击代码中的 Locator，浏览器窗口中会高亮显示对应的页面元素。

如果 Locator 匹配了多个元素，Playwright 会同时高亮所有匹配项。

你可以直接在代码中编辑 Locator，浏览器会实时显示修改后的匹配结果。


## Pick Locator 拾取定位器

点击 Testing Sidebar 底部的 Pick Locator 按钮。

在弹出的浏览器中点击目标元素，VS Code 的 Pick Locator 框中会显示最佳定位器。

按 Enter 复制到剪贴板，粘贴到测试代码中即可。

Playwright 会自动选择最稳定、最语义化的定位方式（优先 role > text > testid）。


## Record New Test 录制新测试

在 Testing Sidebar 点击 Record new 按钮。

Playwright 会打开浏览器窗口，你在其中的所有操作（导航、点击、输入）都会被录制下来。

还可以通过工具栏生成断言：

- Assert visibility —— 断言元素可见
- Assert text —— 断言元素包含文本
- Assert value —— 断言元素的值

录制完成后关闭浏览器，代码会自动生成在 test-1.spec.ts 文件中。


## Record at Cursor 光标处录制

在已有测试代码中将光标放在想要插入操作的位置，点击 Record at cursor。

Playwright 会在浏览器中录制后续操作，并将生成的代码插入到光标所在位置。

这个功能非常适合在已有测试中补充步骤。


## 复习重点

- 能说明 `Playwright VS Code` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
