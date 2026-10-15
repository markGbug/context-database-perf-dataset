# Node.js：使用 VS Code 开发 Node.js

- 来源：[Node.js VS Code](https://www.runoob.com/nodejs/nodejs-vscode.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1001

## 本章内容

Visual Studio Code（简称 VS Code）是微软开发的免费开源代码编辑器， 是目前最受欢迎的 Node.js 开发编辑器之一。


### 主要优势

- 内置 Node.js 支持：提供智能代码补全、调试等功能
- 丰富的扩展：可通过扩展市场安装各种 Node.js 开发工具
- 集成终端：直接在编辑器中运行 Node.js 程序
- 轻量快速：启动速度快，资源占用低


### 安装 VS Code

- 访问 VS Code 官网
- 下载对应操作系统的版本
- 按照安装向导完成安装
- VS Code 完整教程：https://www.runoob.com/vscode/vscode-tutorial.html

另外国内阿里与字节也有基于 VS Code 开发的 AI IDE：


### 扩展推荐

- Node.js Extension Pack：包含多个 Node.js 相关插件的集合包
- JavaScript (ES6) code snippets：提供 ES6+ 代码片段
- Auto Rename Tag：自动重命名 HTML/XML 标签
- ESLint：代码质量检查工具
- Prettier：代码格式化工具
- npm Intellisense：npm 包自动补全
- Path Intellisense：文件路径自动补全


## 创建第一个 Node.js 项目


### 初始化项目

- 打开终端（VS Code 中按 Ctrl+`）
- 创建项目文件夹并进入： mkdir my-node-app cd my-node-app
- 初始化 npm 项目： npm init -y 会生产一个 package.json 的文件：


### 创建主文件

- 在 VS Code 中创建 app.js 文件
- 输入以下代码： 实例 const http = require('http'); const server = http.createServer((req, res) => { res.statusCode = 200; res.setHeader('Content-Type', 'text/plain'); res.end(' RUNOOB Node Test ~ Hello, Node.js!\n'); }); const port = 3000; server.listen(port, () => { console.log(`服务器运行地址：http://localhost:${port}/`); });


### 运行项目

- 在终端中执行： node app.js
- 打开浏览器访问 http://localhost:3000

请注意我们在输入 console. 时，VS Code 的智能感知可以提供代码的建议：


## 调试 Node.js 应用

VS Code 提供了强大的调试功能：


### 配置调试

- 点击左侧活动栏的"运行和调试"图标
- 点击"创建 launch.json 文件"
- 选择"Node.js"环境


### 设置断点

- 在代码行号左侧点击设置断点
- 按 F5 启动调试
- 使用调试工具栏控制执行流程


### 调试控制

- 继续(F5)：继续执行到下一个断点
- 单步跳过(F10)：执行当前行，不进入函数
- 单步调试(F11)：进入函数内部
- 重启(Ctrl+Shift+F5)：重新开始调试
- 停止(Shift+F5)：结束调试


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js VS Code` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
