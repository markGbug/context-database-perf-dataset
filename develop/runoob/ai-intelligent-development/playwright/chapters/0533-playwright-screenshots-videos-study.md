# Playwright：Playwright 截图与视频

- 来源：[Playwright 截图与视频](https://www.runoob.com/playwright/playwright-screenshots-videos.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0533

## 本章内容

本章介绍如何使用 Playwright 进行截图和视频录制，帮助你在测试失败时快速定位问题。


## page.screenshot() 截图


### 全页面截图


## 实例


### 截图选项


## 实例


### 元素截图


## 实例


## 自动截图配置

在配置文件中设置自动截图策略，无需在每个测试中手动调用：


## 实例

失败截图会保存在 test-results/ 目录中，并在 HTML 报告中显示。


## 视频录制


### 配置视频录制


## 实例


### 手动控制视频


## 实例


### 视频录制选项


## 实例


## 截图与视频的使用场景

截图和视频会增加测试执行时间和磁盘占用。推荐仅在生产环境中使用 'only-on-failure' 或 'retain-on-failure'，避免每次都生成媒体文件。


## 复习重点

- 能说明 `Playwright 截图与视频` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
