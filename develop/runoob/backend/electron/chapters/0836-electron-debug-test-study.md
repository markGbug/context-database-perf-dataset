# Electron：Electron 调试与测试

- 来源：[Electron 调试与测试](https://www.runoob.com/electron/electron-debug-test.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0836

## 本章内容

Electron 应用涉及 主进程与渲染进程 两个运行环境，因此调试和测试策略需要针对不同进程设计。 良好的调试与测试流程可以提升开发效率和应用稳定性。


## 调试主进程


### 使用 Chrome DevTools 调试

- Electron 主进程可以通过 --inspect 或 --inspect-brk 启动，用 Chrome DevTools 调试。
- 启动示例：electron --inspect=9222 .
- 在 Chrome 地址栏输入 chrome://inspect，即可连接到主进程进行断点调试、查看调用栈、执行表达式。


### VS Code 断点调试

- 在 VS Code 中配置 launch.json： { "type": "node", "request": "launch", "name": "Electron Main", "program": "${workspaceFolder}/node_modules/electron/cli.js", "args": ["."], "runtimeExecutable": null, "windows": { "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron.cmd" }, "sourceMaps": true, "protocol": "inspector" }
- 这样可以在主进程文件中直接设置断点，调试逻辑和 IPC 通信。


### 日志记录

- 使用 console.log 或第三方日志库（如 winston）记录主进程运行信息。
- 建议日志分类：info、warn、error，方便定位问题。


## 调试渲染进程


### 打开开发者工具

- 在渲染进程中调用： mainWindow.webContents.openDevTools()
- 可直接查看 DOM、JS 调试、网络请求和性能面板。


### 远程调试

- 渲染进程也可开启远程调试端口： electron --remote-debugging-port=9223 .
- 可在 Chrome DevTools 连接远程调试，适合多窗口或跨设备调试。


### React / Vue DevTools

- 对于使用前端框架的渲染进程，安装对应 DevTools： npm install --save-dev electron-devtools-installer
- 示例： const { default: installExtension, REACT_DEVELOPER_TOOLS } = require('electron-devtools-installer') app.whenReady().then(() => { installExtension(REACT_DEVELOPER_TOOLS) .then(name => console.log(`已安装: ${name}`)) .catch(err => console.log('安装失败:', err)) })
- 可调试组件状态、Props、事件，提升前端开发效率。


## 自动化测试


### Spectron 测试框架

- Spectron 是 Electron 官方推荐的端到端测试工具，基于 WebDriver。
- 可测试应用启动、窗口行为、按钮点击、IPC 调用。 npm install --save-dev spectron mocha chai


### 单元测试

- 可针对主进程逻辑、渲染进程模块编写单元测试。
- 推荐使用 Jest 或 Mocha + Chai：npm install --save-dev jest


### 端到端测试

- 测试用户操作流程，如点击按钮、打开新窗口、数据交互是否正常。
- 可结合 Spectron 或 Playwright + Electron。


### CI/CD 集成

在持续集成平台（GitHub Actions、GitLab CI）中配置 Electron 测试：

- 安装 Node.js + Electron
- 执行单元测试和端到端测试
- 生成覆盖率报告并上传


## 小结

Electron 调试与测试核心要点：

- 主进程：Chrome DevTools 或 VS Code 断点调试 + 日志
- 渲染进程：开发者工具 + 前端框架 DevTools
- 自动化测试：Spectron、单元测试、端到端测试 + CI/CD
- 目标：提高开发效率，发现潜在问题，保证应用稳定性


## 复习重点

- 能说明 `Electron 调试与测试` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
