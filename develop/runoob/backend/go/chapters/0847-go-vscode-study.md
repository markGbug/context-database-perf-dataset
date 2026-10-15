# Go：使用 VSCode 开发 Go

- 来源：[Go 开发工具](https://www.runoob.com/go/go-vscode.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：学习笔记
- 章节序号：0847

## 本章内容

Visual Studio Code（简称 VS Code）是一个由微软开发的免费、开源的代码编辑器，支持多种编程语言，并提供了代码高亮、智能代码补全、代码重构、调试等功能。

借助 Visual Studio Code 的 Go 官方扩展插件，你可以获得智能提示、代码跳转、符号检索、单元测试、程序调试等一系列助力 Go 项目开发的实用能力。

如果你还不了解 VS Code 或者还未安装，可以参考：VSCode 教程。


### 安装 Go 插件

打开 VS Code 扩展市场，搜索：Go Extension for VS Code。

编辑器内容，点击左侧的扩展，然后搜索 Go，然后安装官方插件：

安装完成后，我们就可以开始编写 Go 的代码，可以输入 fmt. 试试智能提示功能：


## 智能提示(IntelliSense)

智能提示由 Go 官方团队维护的 gopls 语言服务提供，可通过 gopls 配置项自定义运行规则。


### 1. 语义高亮

VS Code默认基于TextMate语法做代码高亮，如需效果更好的语义级高亮，在配置中开启ui.semanticTokens：

```text
"gopls": { "ui.semanticTokens": true }
```


### 2. 代码自动补全

编辑Go源码时，插件实时弹出代码补全候选，支持当前包、已导入包、尚未导入包的成员联想；输入包名+.即可唤起对应包内方法/常量提示。

快捷键：Ctrl+空格(⌃Space) 手动唤起补全弹窗


### 3. 悬浮文档提示

鼠标悬浮在变量、函数、结构体上，弹窗展示注释文档、函数签名等详情。


### 4. 函数参数提示

键入函数左括号(时自动弹出形参签名，输入实参时下划线跟随切换当前填写参数；

快捷键：Shift+Cmd+空格(⇧⌘Space) 光标在括号内时手动触发参数提示


## 代码导航

编辑器右键菜单内置全套代码导航功能：

- F12 跳转定义：进入类型/变量源码定义处
- 跳转类型定义：定位变量底层的类型源码
- Alt+F12(⌥F12) 预览定义：弹窗预览源码，不切换文件
- Shift+F12(⇧F12) 查找引用：列出当前符号所有被引用位置
- Shift+Alt+H(⇧⌥H) 调用层级：查看函数的调用方与被调用方链路
- Cmd+F12(⌘F12) 查看实现：接口查看所有实现类、实体类查看实现的全部接口

打开命令面板Shift+Cmd+P(⇧⌘P)，通过符号检索快速跳转：

- Shift+Cmd+O(⇧⌘O)：当前文件内检索符号
- Cmd+T(⌘T)：全工作区全局检索符号

使用指令 Go: Toggle Test File，快速在业务代码与对应测试文件来回切换。


## 代码格式化

- 快捷键：Shift+Alt+F(⇧⌥F) 一键格式化当前文件
- 也可通过命令面板/右键菜单执行「格式化文档」


### 格式化配置

- 关闭保存自动格式化 "[go]": { "editor.formatOnSave": false }
- 指定Go插件为Go文件默认格式化工具 "[go]": { "editor.defaultFormatter": "golang.go" }
- 启用gofumpt严格格式化风格（比原生gofmt规范更严苛） "gopls": { "formatting.gofumpt": true } 格式化底层依赖gopls实现


## 单元测试

VS Code侧边栏测试面板 + 代码上方CodeLens快捷按钮，支持函数/文件/包/整个项目的单元测试、基准测试、性能采样。 命令面板输入 Go: test 可查看全部测试指令，常用：

- Go: Test Function At Cursor：运行光标所在函数测试
- Go: Test File：运行当前文件全部测试用例
- Go: Test Package：运行当前代码包全部测试
- Go: Test All Packages in Workspace：全项目批量测试

前3条指令可基于gotests自动生成测试用例骨架；插件支持配置：

- go.testOnSave：保存代码自动执行测试
- go.coverOnSave：保存自动生成测试覆盖率
- go.testFlags：自定义go test运行参数


## 调试Debug

Go插件依托Delve调试器实现Go代码调试，独有能力：

- 本地调试 + 远程服务调试
- 使用Delve表达式语法在调试面板查看自定义数据
- 在调试控制台执行dlv原生指令，动态修改调试配置、查看变量
- 配置hideSystemGoroutines隐藏/展示系统协程
- 右键代码打开汇编视图Disassembly View
- 实验性功能：函数调用调试、core文件分析、Mozilla rr反向调试


## 更多相关工具


## 复习重点

- 能说明 `Go 开发工具` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
