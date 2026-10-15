# Node.js：Node.js 构建简单应用

- 来源：[Node.js 构建简单应用](https://www.runoob.com/nodejs/nodejs-build-app.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1025

## 本章内容

在 Node.js 中构建一个简单应用通常包括以下几个步骤：

- 安装 Node.js
- 设置项目目录
- 初始化项目
- 创建服务器
- 并处理请求和响应

接下来，我们将一步步介绍如何用 Node.js 构建一个简单的 HTTP 应用程序。


### 1、安装 Node.js

首先确保系统上已安装 Node.js 和 npm，可以在命令行中输入以下命令进行验证：

```text
node -v
npm -v
```

如果还未安装，请参考：Node.js 安装配置。


### 2、创建项目文件夹

在终端中，创建一个项目文件夹 my-first-node-app 并进入该文件夹：

```text
mkdir my-first-node-app
cd my-first-node-app
```


### 3、初始化项目

通过 npm init 命令生成 package.json 文件，它包含了项目的配置信息。

运行以下命令并按提示填写信息（可以直接按回车跳过）：

```text
npm init -y
```

把 package.json 文件修改为以下内容：

```text
{
  "name": "my-first-node-app",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {}
}
```


### 4、创建应用入口文件

在项目根目录 my-first-node-app 下创建一个 app.js 文件，这是应用的入口文件，用于设置服务器和处理请求。


### 5、编写服务器代码

在 app.js 文件中编写以下代码，用于创建一个简单的 HTTP 服务器：


## 实例


### 6、运行服务器

在项目根目录下执行以下命令，启动服务器：

```text
npm start
```

你会看到控制台输出如下信息：

```text
Server is running on http://localhost:3000
```


### 7、访问服务器

打开浏览器并访问 http://localhost:3000，你会看到页面显示如下：

说明服务器已经成功运行。


### 8、添加路由

为了处理不同的请求路径，可以在服务器代码中添加简单的路由，例如：


## 实例

通过上述步骤，你已经构建了一个简单的 Node.js 应用，并且可以处理不同的请求路径。

这个基础应用可以进一步扩展，如添加数据库支持、引入 Express 框架处理复杂路由等，为更复杂的项目奠定基础。


## 复习重点

- 能说明 `Node.js 构建简单应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
