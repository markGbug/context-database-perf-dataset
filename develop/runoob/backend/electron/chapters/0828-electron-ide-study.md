# Electron：Electron 开发工具

- 来源：[Electron 开发工具](https://www.runoob.com/electron/electron-ide.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0828

## 本章内容

Electron 开发工具推荐使用 VS Code，如果你还不熟悉 VS Code 可以参考我们的 VS Code 教程。

VS Code 下载地址：https://code.visualstudio.com/。

VS Code 本身就是用 Electron 构建的，因此它对 Electron 开发有天然的支持优势：

- 内置终端集成
- 强大的调试功能
- 丰富的插件生态
- Git 集成
- IntelliSense 智能提示
- 完全免费且开源


### VS Code 必装插件推荐


## Chrome DevTools 调试（渲染进程）

Electron 的渲染进程其实就是一个 Chromium 浏览器页面， 所以你可以像调网页一样，用 Chrome DevTools 直接调试。


### 启用 DevTools

在 main.js 中创建窗口时添加：


## 实例


### 可以调试的内容

- HTML / CSS / JS 代码
- 网络请求（Network）
- 控制台日志（Console）
- DOM 结构
- 性能分析（Performance）
- 内存泄漏（Memory）


### 提示

渲染进程调试几乎与 Chrome 一致，因此：

- 你可以使用 console.log() 输出调试信息
- 也能直接使用 Chrome 的快捷键（Cmd + Option + I / Ctrl + Shift + I）打开 DevTools


## Electron 主进程调试技巧

主进程不是网页，而是 Node.js 环境，调试方式与网页不同。


### 方法 1：使用 VS Code 内置调试器

在项目根目录创建 .vscode/launch.json 文件。

内容如下（可直接用）：

```text
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Electron 主进程调试",
      "type": "node",
      "request": "launch",
      "program": "${workspaceFolder}/node_modules/electron/dist/electron.js",
      "args": ["."],
      "outputCapture": "std",
      "runtimeExecutable": null,
      "cwd": "${workspaceFolder}"
    }
  ]
}
```

然后在 main.js 中设置断点，点击调试 ▶️ 即可。


### 方法 2：命令行远程调试

启动时加上参数：

```text
electron . --inspect=5858
```

然后在 Chrome 地址栏打开：

```text
chrome://inspect
```

即可远程连接主进程，像调 Node.js 一样断点调试。


## 常见调试技巧汇总


## 进阶工具推荐

用 VS Code 写，用 DevTools 看，用 launch.json 调，用 Builder 打包 —— 这就是一个专业 Electron 开发者的完整工具链。


## 复习重点

- 能说明 `Electron 开发工具` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
