# 知识点 12329：Electron：Electron API 速查与配置模板 - electron-builder.yml 模板与说明

- 来源：[Electron API 速查与配置模板](https://www.runoob.com/electron/electron-apis.html)
- 来源章节：[0841-electron-apis-practice.md](../chapters/0841-electron-apis-practice.md)
- 分类：后端开发
- 技术：Electron
- 所在小节：electron-builder.yml 模板与说明
- 知识类型：代码
- 原章节序号：0841

## 原文片段

```text
appId: com.example.myelectronapp
productName: MyElectronApp
directories:
  output: dist
files:
  - "main.js"
  - "preload.js"
  - "renderer/**/*"
win:
  target: nsis
  icon: assets/icon.ico
mac:
  target: dmg
  icon: assets/icon.icns
linux:
  target: AppImage
  icon: assets/
publish:
  provider: github
  repo: my-electron-app
  owner: username
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `electron-builder.yml 模板与说明` 这一小节和 `Electron API 速查与配置模板` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
