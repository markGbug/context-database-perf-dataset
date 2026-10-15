# Python：Python 爬虫 - BeautifulSoup

- 来源：[Python 爬虫](https://www.runoob.com/python3/python-spider-beautifulsoup.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4153

## 本章内容

Python 爬虫（Web Scraping）是指通过编写 Python 程序从互联网上自动提取信息的过程。

爬虫的基本流程通常包括发送 HTTP 请求获取网页内容、解析网页并提取数据，然后存储数据。

Python 的丰富生态使其成为开发爬虫的热门语言，特别是由于其强大的库支持。

一般来说，爬虫的流程可以分为以下几个步骤：

- 发送 HTTP 请求：爬虫通过 HTTP 请求从目标网站获取 HTML 页面，常用的库包括 requests。
- 解析 HTML 内容：获取 HTML 页面后，爬虫需要解析内容并提取数据，常用的库有 BeautifulSoup、lxml、Scrapy 等。
- 提取数据：通过定位 HTML 元素（如标签、属性、类名等）来提取所需的数据。
- 存储数据：将提取的数据存储到数据库、CSV 文件、JSON 文件等格式中，以便后续使用或分析。

本章节主要介绍 BeautifulSoup，它是一个用于解析 HTML 和 XML 文档的 Python 库，能够从网页中提取数据，常用于网页抓取和数据挖掘。


## BeautifulSoup

BeautifulSoup 是一个用于从网页中提取数据的 Python 库，特别适用于解析 HTML 和 XML 文件。

BeautifulSoup 能够通过提供简单的 API 来提取和操作网页中的内容，非常适合用于网页抓取和数据提取的任务。


### 安装 BeautifulSoup

要使用 BeautifulSoup，需要安装 beautifulsoup4 和 lxml 或 html.parser（一个 HTML 解析器）。

我们可以使用 pip 来安装这些依赖：

```text
pip install beautifulsoup4
pip install lxml  # 推荐使用 lxml 作为解析器（速度更快）
```

如果你没有 lxml，可以使用 Python 内置的 html.parser 作为解析器。


### 基本用法

BeautifulSoup 用于解析 HTML 或 XML 数据，并提供了一些方法来导航、搜索和修改解析树。

BeautifulSoup 常见的操作包括查找标签、获取标签属性、提取文本等。

要使用 BeautifulSoup，需要先导入 BeautifulSoup，并将 HTML 页面加载到 BeautifulSoup 对象中。

通常，你会先用爬虫库（如 requests）获取网页内容:


## 实例

获取网页标题：


## 实例

执行以上代码，输出标题为：

```text
搜索 - Microsoft 必应
```


### 中文乱码问题

使用 requests 库抓取中文网页时，可能会遇到编码问题，导致中文内容无法正确显示，为了确保能够正确抓取并显示中文网页，通常需要处理网页的字符编码。

自动检测编码 requests 通常会自动根据响应头中的 Content-Type 来推测网页的编码，但有时可能不准确，此时可以使用 chardet 来自动检测编码。


## 实例

执行以上代码，输出为：

```text
utf-8
```

如果你知道网页的编码（例如 utf-8 或 gbk），可以直接设置 response.encoding:

```text
response.encoding = 'utf-8'  # 或者 'gbk'，根据实际情况选择
```


### 查找标签

BeautifulSoup 提供了多种方法来查找网页中的标签，最常用的包括 find() 和 find_all()。

- find() 返回第一个匹配的标签
- find_all() 返回所有匹配的标签


## 实例

输出结果类似如下：

```html
<a class="mnav" href="http://news.baidu.com" name="tj_trnews">新闻</a>
----------------------------
http://news.baidu.com
----------------------------
[<a class="mnav" href="http://news.baidu.com" name="tj_trnews">新闻</a>, <a class="mnav" href="https://www.hao123.com" name="tj_trhao123">hao123</a>, <a class="mnav" href="http://map.baidu.com" name="tj_trmap">地图</a>, <a class="mnav" href="http://v.baidu.com" name="tj_trvideo">视频</a>,
```


### 获取标签的文本

通过 get_text() 方法，你可以提取标签中的文本内容：


## 实例

输出结果类似如下：

```text
 百度一下，你就知道
...
```


### 查找子标签和父标签

```text
# 获取当前标签的父标签
parent_tag = first_link.parent

# 获取当前标签的所有子标签
children = first_link.children
```


## 实例

输出结果类似如下：

```html
<a class="mnav" href="http://news.baidu.com" name="tj_trnews">新闻</a>
----------------------------
 新闻 hao123 地图 视频 贴吧  登录   更多产品
```


### 查找具有特定属性的标签

你可以通过传递属性来查找具有特定属性的标签。

例如，查找类名为 example-class 的所有 div 标签：

```html
# 查找所有 class="example-class" 的 <div> 标签
divs_with_class = soup.find_all('div', class_='example-class')

# 查找具有 id="unique-id" 的 <p> 标签
unique_paragraph = soup.find('p', id='unique-id')
```

获取搜索按钮，id 为 su ：


## 实例

输出结果为：

```text
百度一下
```


## 高级用法


### CSS 选择器

BeautifulSoup 也支持通过 CSS 选择器来查找标签。

select() 方法允许使用类似 jQuery 的选择器语法来查找标签：

```html
# 使用 CSS 选择器查找所有 class 为 'example' 的 <div> 标签
example_divs = soup.select('div.example')

# 查找所有 <a> 标签中的 href 属性
links = soup.select('a[href]')
```


### 处理嵌套标签

BeautifulSoup 支持深度嵌套的 HTML 结构，你可以通过递归查找子标签来处理这些结构：

```html
# 查找嵌套的 <div> 标签
nested_divs = soup.find_all('div', class_='nested')
for div in nested_divs:
    print(div.get_text())
```


### 修改网页内容

BeautifulSoup 允许你修改 HTML 内容。

我们可以修改标签的属性、文本或删除标签：


## 实例


### 转换为字符串

你可以将解析的 BeautifulSoup 对象转换回 HTML 字符串：

```text
# 转换为字符串
html_str = str(soup)
```


## BeautifulSoup 属性与方法

以下是 BeautifulSoup 中常用的属性和方法:


### 其他属性


### 其他


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 爬虫` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
