# Selenium：Selenium WebDriver

- 来源：[Selenium WebDriver](https://www.runoob.com/selenium/selenium-webdriver.html)
- 分类：AI / 智能开发
- 技术：Selenium
- 笔记类型：练习笔记
- 章节序号：0604

## 本章内容

Selenium WebDriver 是 Selenium 的核心组件，它提供了与浏览器交互的 API，允许开发者通过编程语言控制浏览器并执行各种操作。


### 启动浏览器

Selenium WebDriver 支持多种浏览器（如 Chrome、Firefox、Edge 等）。

启动浏览器前，需要下载并配置对应的浏览器驱动（如 ChromeDriver、GeckoDriver 等），详细可参见 selenium 安装。

启动浏览器的代码示例（Python）。

在 Selenium 4 中，引入了 Service 对象来设置驱动程序路径，这种方式更加灵活，且符合 Selenium 4 的设计规范。


## Selenium 4 实例

- 导入所需的模块（webdriver 和 ChromeService）。
- 创建 ChromeService 对象，指定 ChromeDriver 的路径。
- 创建 ChromeOptions 对象，用于配置浏览器的启动选项。
- 使用 webdriver.Chrome() 启动 Chrome 浏览器，并传入 service 和 options 参数。

在 Selenium 3 及之前的版本中，通常直接在 webdriver.Chrome() 中设置驱动程序路径，例如：


## Selenium 3 实例


### 关闭浏览器

使用 quit() 方法关闭浏览器并结束 WebDriver 会话。

```text
driver.quit()
```


### 打开和关闭网页

使用 get() 方法打开指定的 URL。

```text
driver.get("https://www.example.com")
```


### 关闭当前标签页

使用 close() 方法关闭当前标签页。

```text
driver.close()
```

如果只有一个标签页，close() 会关闭浏览器。


## 浏览器窗口操作


### 最大化窗口

使用 maximize_window() 方法将浏览器窗口最大化。

```text
driver.maximize_window()
```


### 最小化窗口

使用 minimize_window() 方法将浏览器窗口最小化。

```text
driver.minimize_window()
```


### 设置窗口大小

使用 set_window_size(width, height) 方法设置浏览器窗口的大小。

```text
driver.set_window_size(1024, 768)  # 设置窗口大小为 1024x768 像素
```


### 全屏模式

使用 fullscreen_window() 方法将浏览器窗口设置为全屏模式。

```text
driver.fullscreen_window()
```


## 页面导航


### 前进和后退

使用 back() 方法返回上一个页面。

使用 forward() 方法前进到下一个页面。

```text
driver.get("https://www.baidu.com")
driver.get("https://www.runoob.com")

driver.back()    # 返回 baidu.com
driver.forward() # 前进到 runoob.com
```


### 刷新页面

使用 refresh() 方法刷新当前页面。

```text
driver.refresh()
```


## 取页面标题和 URL


### 获取页面标题

使用 title 属性获取当前页面的标题。

```text
title = driver.title
print("页面标题:", title)
```


### 获取当前 URL

使用 current_url 属性获取当前页面的 URL。

```text
url = driver.current_url
print("当前 URL:", url)
```


## 综合示例


## 实例

以上代码执行后会执行以下步骤：

- 启动 Chrome 浏览器。
- 打开指定网页（https://www.runoob.com）。
- 最大化浏览器窗口。
- 获取并打印页面标题和 URL。
- 导航到另一个网页（https://www.jyshare.com）。
- 返回上一个页面。
- 刷新当前页面。
- 关闭浏览器。

输出结果为：

```text
页面标题: 菜鸟教程 - 学的不仅是技术，更是梦想！
当前 URL: https://www.runoob.com/
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Selenium WebDriver` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
