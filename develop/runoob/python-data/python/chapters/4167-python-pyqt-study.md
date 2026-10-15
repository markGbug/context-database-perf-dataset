# Python：Python PyQt

- 来源：[Python PyQt](https://www.runoob.com/python3/python-pyqt.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4167

## 本章内容

PyQt 是一个强大的 Python 库，用于创建图形用户界面（GUI），可以用来代替 Python 内置的 Tkinter。

PyQt 是 Qt 框架的 Python 绑定，广泛应用于桌面应用程序开发。

Qt 是一个跨平台的 C++ 应用程序开发框架。

PyQt 允许 Python 开发者利用 Qt 库创建功能强大的 GUI 应用程序。

PyQt 有以下几个主要版本：

- PyQt4：基于 Qt4 的绑定
- PyQt5：基 于Qt5 的绑定
- PyQt6：基于 Qt6 的绑定（最新版本）


### 安装 PyQt

使用 pip 安装 PyQt5：

```text
# 安装PyQt5
pip install PyQt5

# 安装Qt设计师和其他工具（可选）
pip install PyQt5-tools
```


## 第一个 PyQt 程序


### 创建简单窗口

以下是一个最基本的 PyQt 程序，创建一个空白窗口：


## 实例


### 代码解析

- QApplication：管理 GUI 应用程序的控制流和主设置。
- QWidget：最基本的窗口类，所有 UI 组件都继承自它。
- setWindowTitle()：设置窗口标题。
- setGeometry()：设置窗口位置和大小。
- show()：显示窗口。
- app.exec_()：启动事件循环，等待用户交互。

一个典型的PyQt应用程序包含以下部分：

- QApplication对象：每个PyQt应用程序都需要有一个QApplication实例
- 窗口和控件：用户界面组件
- 事件循环：处理用户输入和系统事件的循环
- 事件处理器：响应事件的函数或方法


## 实例


## 常用 PyQt 组件


### 按钮（QPushButton）


## 实例


### 标签（QLabel）


## 实例


### 文本框（QLineEdit）


## 实例

更多常用组件内容参考：https://www.runoob.com/python3/python-pyqt-widgets.html


## 布局管理（QVBoxLayout）

使用布局管理器可以自动调整组件位置：


## 实例

更多布局管理内容参考：https://www.runoob.com/python3/python-pyqt-layout.html


## 信号与槽机制

PyQt 使用信号（Signal）和槽（Slot）机制处理事件。

PyQt 的信号和槽机制是用于对象之间通信的核心机制。

- 信号(Signal): 当特定事件发生时发出的通知
- 槽(Slot): 响应信号的函数或方法


## 实例


### 自定义信号


## 实例

更多布局管理内容参考：https://www.runoob.com/python3/python-pyqt-signals-and-slots.html


## 使用 Qt Designer

Qt Designer 是一个可视化设计工具，可以拖放组件来设计界面：

- 启动 Designer (通常在 Python 安装目录的 Lib\site-packages\qt5_applications\Qt\bin 下)
- 设计界面并保存为 .ui 文件
- 将 .ui 文件转换为 Python 代码： pyuic5 input.ui -o output.py

在代码中使用生成的界面：


## 实例


## 实战：简单的记事本应用


### 界面设计


## 实例


## 后续章节

- PyQt5 核心组件
- 学习资源

## 复习重点

- 能说明 `Python PyQt` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
