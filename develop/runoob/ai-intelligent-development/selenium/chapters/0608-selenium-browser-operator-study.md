# Selenium：Selenium 浏览器操作

- 来源：[Selenium 浏览器操作](https://www.runoob.com/selenium/selenium-browser-operator.html)
- 分类：AI / 智能开发
- 技术：Selenium
- 笔记类型：学习笔记
- 章节序号：0608

## 本章内容

Selenium 不仅可以操作网页元素，还可以控制浏览器本身的行为，例如管理窗口、处理弹窗、操作 Cookies、执行 JavaScript 等。

以下是 Selenium 中常用的浏览器操作及其说明:


## 1. 处理浏览器弹窗（alert、confirm、prompt）

在 Web 应用程序中，弹窗（如 alert、confirm、prompt）是常见的用户交互方式。Selenium 提供了 Alert 类来处理这些弹窗。


### 1.1 处理 alert 弹窗

alert 弹窗通常用于显示一条消息，用户只能点击"确定"按钮关闭弹窗。


## 实例


### 1.2 处理 confirm 弹窗

confirm 弹窗通常用于确认操作，用户可以选择"确定"或"取消"。


## 实例


### 1.3 处理 prompt 弹窗

prompt 弹窗通常用于获取用户输入，用户可以输入文本并选择"确定"或"取消"。


## 实例


## 2. 切换窗口和标签页

在 Web 应用程序中，用户可能会打开多个窗口或标签页。Selenium 提供了 switch_to.window() 方法来切换窗口或标签页。


### 2.1 切换窗口


## 实例


### 2.2 切换标签页

切换标签页与切换窗口类似，因为每个标签页都是一个独立的窗口句柄。


## 实例


## 3. 处理 iframe

iframe 是嵌入在网页中的另一个网页。Selenium 提供了 switch_to.frame() 方法来切换到 iframe。


### 3.1 切换到 iframe


## 实例


### 3.2 切换回主页面

在 iframe 中操作完成后，可以使用 switch_to.default_content() 方法切换回主页面。


## 实例


## 4. 浏览器 Cookies 操作

Selenium 提供了 get_cookies()、add_cookie()、delete_cookie() 等方法来操作浏览器的 Cookies。


### 4.1 获取 Cookies


## 实例


### 4.2 添加 Cookie


## 实例


### 4.3 删除 Cookie


## 实例


## 后续章节

- 5. 执行 JavaScript 代码
- 5.1 执行 JavaScript 代码
- 实例
- 5.2 获取 JavaScript 返回值
- 实例
- 6. 综合示例
- 实例

## 复习重点

- 能说明 `Selenium 浏览器操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
