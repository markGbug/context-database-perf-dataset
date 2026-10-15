# Electron：Electron 实战项目

- 来源：[Electron 实战项目](https://www.runoob.com/electron/electron-practical.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0839

## 本章内容

通过实战项目，可以加深对 Electron 各种特性的理解，包括窗口管理、IPC 通信、文件操作、数据存储和界面优化。


## 项目一：桌面笔记应用


### 功能设计

- 创建、编辑、删除笔记
- 自动保存与本地存储
- 支持多窗口同时编辑
- 界面简洁，提供 Markdown 渲染


### 技术选型

- 前端框架：Vue 或 React
- 渲染进程：展示笔记内容，支持富文本 / Markdown
- 数据存储：electron-store 保存笔记数据
- 主进程：管理窗口、菜单和快捷键
- IPC 通信：渲染进程请求主进程读取或保存数据


### 实现步骤

1、创建 Electron 项目

```text
mkdir electron-notes
cd electron-notes
npm init -y
npm install electron electron-store
```

2、主进程 main.js


## 实例

3、预加载脚本 preload.js


## 实例

4、渲染进程 index.html


## 实例


### 代码解析

- electron-store：负责本地数据存储，自动序列化 JSON
- ipcMain.handle / ipcRenderer.invoke：实现渲染进程与主进程通信
- contextBridge：安全暴露 API 给渲染进程
- textarea + 按钮：简单实现笔记内容编辑与保存


## 项目二：文件管理器


### 界面设计

- 左侧目录树，右侧文件列表
- 支持文件操作：新增、删除、重命名
- 拖拽文件到目标目录
- 简单搜索和排序功能


### 文件操作实现

- Node.js fs 模块：读取、写入、删除文件
- path 模块：路径处理
- IPC 通信：渲染进程请求主进程进行文件操作


## 实例


## 实例


### 拖拽功能

- 渲染进程监听 dragstart 和 drop 事件
- 主进程使用 fs.rename 或 fs.copyFile 移动文件


## 实例


### 性能优化

- 对大目录采用异步读取，避免阻塞渲染进程
- 文件列表虚拟化，减少 DOM 渲染压力
- 对频繁操作使用批量更新或 Web Worker


## 小结

通过这两个实战项目，你可以掌握：

- 窗口与多进程通信：父子窗口、IPC
- 本地数据存储：electron-store、fs
- 界面与性能优化：虚拟列表、懒加载、异步处理
- 原生功能集成：文件操作、拖拽、菜单和快捷键

这些项目可以作为后续复杂桌面应用开发的基础模板，帮助快速搭建功能齐全的 Electron 应用。


## 复习重点

- 能说明 `Electron 实战项目` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
