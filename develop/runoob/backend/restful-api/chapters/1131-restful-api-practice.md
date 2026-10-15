# RESTful API：RESTful API 教程

- 来源：[RESTful API 教程](https://www.runoob.com/restfulapi/restful-api-tutorial.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：练习笔记
- 章节序号：1131

## 本章内容

在现代 Web 开发中，RESTful API 已成为应用程序之间通信的标准方式。

REST（Representational State Transfer，表述性状态转移）是一种软件架构风格，由 Roy Fielding 博士在 2000 年提出。

REST 定义了一组约束条件和原则，用于创建可扩展、松耦合的 Web 服务。

RESTful API 是遵循 REST 架构风格设计的 API。它使用HTTP协议的特性，通过 URL 定位资源，用 HTTP 方法（GET、POST等）描述操作，实现客户端与服务器之间的交互。


## 谁适合阅读本教程？

无论你是前端开发者需要与后端 API 交互，还是后端开发者需要设计 API 接口，掌握 RESTful API 都是必备技能。


## RESTful API 特点？

关键特点：

- 无状态：每个请求包含处理所需的所有信息
- 统一接口：使用标准 HTTP 方法进行操作
- 资源导向：所有内容都被抽象为资源
- 可缓存：响应应明确是否可缓存


## RESTful API的核心原则


### 1. 资源与URI

在REST中，所有事物都被抽象为资源，每个资源有唯一的标识符（URI）。

URI设计规范：

- 使用名词而非动词表示资源
- 使用复数形式命名集合
- 使用小写字母和连字符(-)
- 避免文件扩展名

示例：

```text
/users          # 用户集合
/users/123      # ID为123的用户
/users/123/orders  # 用户123的订单集合
```


### 2. HTTP方法的使用

RESTful API充分利用HTTP方法的语义：


### 3. 无状态性

每个请求必须包含处理所需的所有信息，服务器不保存客户端状态。这使得API易于扩展和负载均衡。


### 4. 表述形式

资源可以有多种表述形式（如JSON、XML），客户端通过Accept头指定需要的格式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RESTful API 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
