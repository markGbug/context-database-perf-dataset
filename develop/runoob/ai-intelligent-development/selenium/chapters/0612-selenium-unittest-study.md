# Selenium：Selenium测试框架集成

- 来源：[Selenium 测试框架集成](https://www.runoob.com/selenium/selenium-unittest.html)
- 分类：AI / 智能开发
- 技术：Selenium
- 笔记类型：学习笔记
- 章节序号：0612

## 本章内容

Selenium 可以与多种测试框架集成，例如 unittest 和 pytest，从而实现更结构化的测试代码管理和测试报告生成。


## 与 unittest 集成

unittest 是 Python 标准库中的一个测试框架，它提供了丰富的断言方法和测试组织方式。

我们可以将 Selenium 与 unittest 集成，以编写结构化的测试用例。


### 基本结构

以下是一个简单的 Selenium 与 unittest 集成的示例：


## 实例


### 代码解析

- setUp 方法：在每个测试用例执行之前运行，用于初始化测试环境。在这里，我们启动浏览器并打开Google首页。
- test_search 方法：这是一个测试用例，用于测试Google搜索功能。我们找到搜索框，输入"Selenium"，然后提交搜索。最后，我们断言页面标题中是否包含"Selenium"。
- tearDown 方法：在每个测试用例执行之后运行，用于清理测试环境。在这里，我们关闭浏览器。


### 运行测试

可以通过以下命令运行测试：

```text
python -m unittest test_baidu_search.py
```


## 与 pytest 集成

pytest 是另一个流行的Python测试框架，它提供了更简洁的语法和更强大的功能。我们可以将Selenium与pytest集成，以编写更灵活的测试用例。


### 基本结构

以下是一个简单的Selenium与pytest集成的示例：


## 实例


### 代码解析

- browser 夹具：这是一个pytest夹具，用于在每个测试用例执行之前启动浏览器，并在测试用例执行之后关闭浏览器。
- test_baidu_search 函数：这是一个测试用例，用于测试Google搜索功能。我们找到搜索框，输入"Selenium"，然后提交搜索。最后，我们断言页面标题中是否包含"Selenium"。


### 运行测试

可以通过以下命令运行测试：

```text
pytest test_baidu_search.py
```


## 生成测试报告

在自动化测试中，生成测试报告是非常重要的。我们可以使用pytest-html插件来生成HTML格式的测试报告。


### 安装 pytest-html

可以通过以下命令安装pytest-html插件：


## 实例


### 生成测试报告

在运行测试时，可以通过以下命令生成HTML格式的测试报告：

```text
pytest --html=report.html
```

生成的report.html文件将包含测试的详细结果，包括通过的测试用例、失败的测试用例以及错误信息。


## 测试代码

Selenium 4 引入了许多新特性，如相对定位器、改进的窗口管理、更好的 DevTools 支持等：


## 实例


## 复习重点

- 能说明 `Selenium 测试框架集成` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
