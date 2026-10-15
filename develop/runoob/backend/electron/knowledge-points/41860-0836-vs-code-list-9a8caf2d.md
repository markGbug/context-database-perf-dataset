# 知识点 41860：Electron：Electron 调试与测试 - VS Code 断点调试

- 来源：[Electron 调试与测试](https://www.runoob.com/electron/electron-debug-test.html)
- 来源章节：[0836-electron-debug-test-practice.md](../chapters/0836-electron-debug-test-practice.md)
- 分类：后端开发
- 技术：Electron
- 所在小节：VS Code 断点调试
- 知识类型：要点
- 原章节序号：0836

## 原文片段

在 VS Code 中配置 launch.json： { "type": "node", "request": "launch", "name": "Electron Main", "program": "${workspaceFolder}/node_modules/electron/cli.js", "args": ["."], "runtimeExecutable": null, "windows": { "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron.cmd" }, "sourceMaps": true, "protocol": "inspector" }

## 学习理解

这是一个列表型要点，通常用于总结特性、规则、组成部分或注意事项。复习时要把它放回本章上下文。

- 它属于哪一类规则或特性？
- 和同组其他要点有什么区别？
- 有没有可以补充的例子或反例？

## 复习问题

- `VS Code 断点调试` 这一小节和 `Electron 调试与测试` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
