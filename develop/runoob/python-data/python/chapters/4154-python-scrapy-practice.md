# Python：Python Scrapy 库

- 来源：[Python Scrapy 库](https://www.runoob.com/python3/python-scrapy.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4154

## 本章内容

Scrapy 是一个功能强大的 Python 爬虫框架，专门用于抓取网页数据并提取信息。

Scrapy常被用于数据挖掘、信息处理或存储历史数据等应用。

Scrapy 内置了许多有用的功能，如处理请求、跟踪状态、处理错误、处理请求频率限制等，非常适合进行高效、分布式的网页爬取。

与简单的爬虫库（如 requests 和 BeautifulSoup）不同，Scrapy 是一个全功能的爬虫框架，具有高度的可扩展性和灵活性，适用于复杂和大规模的网页抓取任务。

Scrapy 官网：https://scrapy.org/。

Scrapy 特点与介绍：https://www.runoob.com/w3cnote/scrapy-detail.html。

Scrapy 架构图(绿线是数据流向):

Scrapy 的工作基于以下几个核心组件：

- Spider：爬虫类，用于定义如何从网页中提取数据以及如何跟踪网页的链接。
- Item：用来定义和存储抓取的数据。相当于数据模型。
- Pipeline：用于处理抓取到的数据，常用于清洗、存储数据等操作。
- Middleware：用来处理请求和响应，可以用于设置代理、处理 cookies、用户代理等。
- Settings：用来配置 Scrapy 项目的各项设置，如请求延迟、并发请求数等。


### 安装 Scrapy

在使用 Scrapy 之前，你需要先安装它，我们使用 pip 安装：

```text
pip install scrapy
```


### Scrapy 项目结构

Scrapy 项目是一个结构化的目录，其中包含多个文件夹和模块，旨在帮助你组织爬虫的代码。

Scrapy 使用命令行工具来创建和管理爬虫项目。你可以使用以下命令创建一个新的 Scrapy 项目：

```text
scrapy startproject myproject
```

这将创建一个名为 myproject 的项目，项目结构大致如下：

```text
myproject/
    scrapy.cfg            # 项目的配置文件
    myproject/            # 项目源代码文件夹
        __init__.py
        items.py          # 定义抓取的数据结构
        middlewares.py    # 定义中间件
        pipelines.py      # 定义数据处理管道
        settings.py       # 项目的设置文件
        spiders/           # 存放爬虫代码的文件夹
            __init__.py
            myspider.py   # 自定义的爬虫代码
```


## 编写一个简单的 Scrapy 爬虫

以下是一个基本的 Scrapy 爬虫示例，展示了如何从网页中抓取数据。

我们创建一个爬虫项目：

```text
scrapy startproject runoob_test_spiders
```

执行以上命令，如果成功会输出：

```text
templates/project', created in:/Users/Runoob/runoob-test/runoob_test_spiders

You can start your first spider with:
    cd runoob_test_spiders
    scrapy genspider example example.com
```

生成的项目结构如下：

然后进入该目录：

```text
cd runoob_test_spiders
```

接下来通过 scrapy genspider 命令来创建一个爬虫：

```text
scrapy genspider douban_spider movie.douban.com
```

目录结构如下：

runoob_test_spiders 目录下生成一个名为 douban_spider.py 的文件，代码如下：


## 实例

代码说明：

- name：定义爬虫的名称，必须是唯一的。
- allowed_domains：限制爬虫的访问域名，防止爬虫爬取其他域名的网页。
- start_urls：定义爬虫的起始页面，爬虫将从这些页面开始抓取。
- parse：parse 方法是每个爬虫的核心部分，用于处理响应并提取数据。它接收一个 response 对象，表示服务器返回的页面内容。


### 编写爬虫代码

编写爬虫代码前我们需要注意几个点：

- 豆瓣等网站可能会检测爬虫行为，建议设置 USER_AGENT 和 DOWNLOAD_DELAY 来模拟正常用户行为。
- 在爬取数据时，请遵守目标网站的 robots.txt 文件规定，避免对服务器造成过大压力。
- 如果频繁爬取，可能会触发 IP 封禁。


### 修改 settings.py 配置

在 settings.py 中添加以下配置，以模拟浏览器请求并绕过反爬虫机制：

```text
# 设置 User-Agent
USER_AGENT = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'

# 不遵守 robots.txt 规则
ROBOTSTXT_OBEY = False

# 设置下载延迟，避免过快请求
DOWNLOAD_DELAY = 2

# 启用自动限速扩展
AUTOTHROTTLE_ENABLED = True
AUTOTHROTTLE_START_DELAY = 2
AUTOTHROTTLE_MAX_DELAY = 5
```

在爬虫代码中，添加自定义请求头（如 User-Agent 和 Referer），以进一步模拟浏览器行为。

打开 douban_spider.py 文件，并修改其内容如下：


## 实例

代码解析：

- name = "douban_spider": 定义爬虫的名称。
- start_urls: 定义爬虫开始爬取的初始 URL（豆瓣电影 Top 250 页面）。
- parse 方法:使用 CSS 选择器提取每部电影的标题、评分和简介。span.title::text：提取电影标题。span.rating_num::text：提取电影评分。span.inq::text：提取电影简介。
- 分页处理:使用 span.next a::attr(href) 提取下一页的链接。如果存在下一页，使用 response.follow 继续爬取。

在命令行中运行以下命令来启动爬虫：

```text
scrapy crawl douban_spider -o douban_movies.csv
```

这将启动爬虫并将提取的数据保存到 douban_movies.csv 文件中。

注意：以上内容仅供学习，在爬取数据时，请遵守目标网站的 robots.txt 文件规定。


## 常用方法


### 1. 爬虫方法


### 2. 数据提取方法


### 3. 请求与响应方法


### 4. 中间件与管道方法


### 5. 工具与扩展方法


### 6. 常用设置（settings.py）


### 7. 其他常用方法

以上表格列出了 Scrapy 中常用的方法及其作用。这些方法涵盖了爬虫开发的各个方面，包括请求生成、数据提取、中间件处理、管道操作等。通过掌握这些方法，你可以高效地编写和管理 Scrapy 爬虫。如果需要更详细的功能，可以参考 Scrapy 官方文档。


## 方法使用举例


### 1. start_requests()

start_requests() 方法是 Scrapy 爬虫的入口点，用于生成初始请求。通常在这个方法中定义爬虫的起始 URL。


## 实例


### 2. parse()

parse() 方法是默认的响应处理方法，用于解析响应并提取数据或生成新的请求。


## 实例


### 3. parse_item()

parse_item() 方法用于解析单个项目（Item）的响应，通常用于提取结构化数据。


## 实例


### 4. follow()

follow() 方法用于生成新的请求并自动处理响应，通常用于跟踪链接。


## 实例


## 后续章节

- 5. yield
- 实例
- 6. Item
- 实例
- 7. ItemLoader
- 实例
- 8. Request
- 实例
- 9. Response
- 实例
- 10. Selector
- 实例
- 11. CrawlSpider
- 实例
- 12. LinkExtractor
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python Scrapy 库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
