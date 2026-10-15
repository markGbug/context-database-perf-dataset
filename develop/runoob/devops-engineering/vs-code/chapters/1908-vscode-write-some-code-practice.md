# VS Code：VSCode 编写代码

- 来源：[VSCode 编写代码](https://www.runoob.com/vscode/vscode-write-some-code.html)
- 分类：DevOps / 工程化
- 技术：VS Code
- 笔记类型：练习笔记
- 章节序号：1908

## 本章内容

VS Code 内置了对 JavaScript、TypeScript、HTML、CSS 等多种语言的支持。

在本章节中，我们将创建一个 JavaScript 代码文件，并使用 VS Code 提供的一些代码编辑功能。

VS Code 支持多种编程语言，在后面的章节中，我们还会安装 Python 的语言扩展，为其他语言添加支持。


### 1、创建 JavaScript 文件并编写代码

在资源管理器（Explorer）视图中，创建一个名为 app.js 的新文件，并输入以下 JavaScript 代码：


## 实例

代码自动补全（IntelliSense）：当您开始输入代码时，会弹出代码补全建议，使用方向键 ↑ 或 ↓（上下键） 导航建议项，按 Tab 键选择并插入选中的建议。

语法高亮：注意代码的格式化显示（语法高亮），这有助于区分代码的不同部分，提高可读性。


### 使用代码操作（Code Actions）

将光标放在字符串 'Hello,' 上时，您会看到一个小灯泡图标，表示可以应用代码操作（Code Action）。

您也可以使用快捷键 ⌃Space 打开灯泡菜单。

点击灯泡图标，然后选择 Convert to template string（转换为模板字符串）。

代码操作为您的代码提供了快速修复建议。

在本例中，Code Action 将字符串拼接：

```text
"Hello, " + name
```

转换为模板字符串：

```text
`Hello, ${name}`
```

模板字符串是 JavaScript 中一种特殊的语法，可以在字符串中嵌入表达式。

转化后的代码如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `VSCode 编写代码` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
