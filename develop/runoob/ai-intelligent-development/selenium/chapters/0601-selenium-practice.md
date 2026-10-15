# Selenium：Selenium 教程

- 来源：[Selenium 教程](https://www.runoob.com/selenium/selenium-tutorial.html)
- 分类：AI / 智能开发
- 技术：Selenium
- 笔记类型：练习笔记
- 章节序号：0601

## 本章内容

Selenium 是一个用于自动化 Web 浏览器操作的工具集。

Selenium主要用于 Web 应用程序的自动化测试。

Selenium支持多种编程语言（如 Python、Java、C#、JavaScript 等），并且可以在多种浏览器（如 Chrome、Firefox、Edge、Safari 等）和操作系统（如 Windows、macOS、Linux）上运行。

Selenium 的核心功能是模拟用户在浏览器中的操作，例如点击按钮、输入文本、导航页面等。


## 谁适合阅读本教程？

- 软件测试工程师
- 开发人员（前端、后端、全栈）
- 数据分析师和数据科学家
- DevOps 工程师
- 学生和编程爱好者
- 技术经理和团队负责人
- 创业者和产品经理

Selenium 是一个功能强大的自动化测试工具，适用于 Web 应用程序的自动化测试和其他浏览器自动化任务。

通过 Selenium，你可以编写脚本来模拟用户在浏览器中的操作，从而提高测试效率。


## 阅读本教程前，您需要了解的知识：

- 编程基础（如 Python、Java、JavaScript 等）
- Web 开发基础（HTML、CSS、JavaScript）
- 浏览器开发者工具（如 Chrome DevTools）
- 版本控制工具（如 Git，可选）
- 测试基础（如单元测试、断言，可选）
- 操作系统和命令行基础
- 学习资源（官方文档、教程、书籍）


## 学习路径

- 学习编程基础（如 Python 或 Java）。
- 学习 Web 开发基础（HTML、CSS、JavaScript）。
- 熟悉浏览器开发者工具。
- 学习 Selenium 基础（环境搭建、元素定位、元素操作）。
- 实践项目（如自动化登录、表单提交、数据抓取等）。
- 学习高级主题（如等待机制、浏览器操作、测试框架集成）。


## 编写第一个 Selenium 脚本

下面是一个使用 Python 编写的简单 Selenium 脚本示例，这个脚本会打开 Chrome 浏览器，访问百度首页，并在搜索框中输入 "Runoob" 并点击搜索按钮。


## 实例


### 代码解析

- webdriver.Chrome()：创建一个 Chrome WebDriver 实例。
- driver.get("https://www.baidu.com")：打开百度首页。
- driver.find_element_by_name("wd")：查找页面中 name 属性为 "wd" 的元素（即搜索框）。
- search_box.send_keys("Runoob")：在搜索框中输入 "Runoob"。
- search_box.send_keys(Keys.RETURN)：模拟按下回车键，触发搜索。
- driver.quit()：关闭浏览器。


## 相关链接

官网：https://www.selenium.dev/

Selenium 下载：https://www.selenium.dev/downloads/

Selenium 中文文档： https://www.selenium.dev/zh-cn/documentation/

Github 开源地址：https://github.com/SeleniumHQ


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Selenium 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
