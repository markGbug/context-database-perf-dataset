# React：React 项目说明

- 来源：[React 项目说明](https://www.runoob.com/react/react-project-intro.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3040

## 本章内容

一个典型的 React 项目由多个文件和文件夹组成，每个部分都有其特定的作用。

本章节将对 React 项目代码做基本的说明，帮助大家理解项目的结构和各个部分的功能。

- React 项目由多个文件和文件夹组成，核心文件包括 index.html、index.js 和 App.js。
- React 组件是应用的基本构建块，可以是函数组件或类组件。
- JSX 是 React 的核心语法，用于描述 UI。
- Props 和 State 是 React 组件中管理数据的主要方式。


### 项目结构

一个 React 项目通常包含以下文件和文件夹：

```text
my-react-app/
├── node_modules/       # 项目依赖的第三方库
├── public/             # 静态资源文件夹
│   ├── index.html      # 应用的 HTML 模板
│   └── ...             # 其他静态资源（如图片、字体等）
├── src/                # 项目源代码
│   ├── App.js          # 主组件
│   ├── App.css         # 主组件的样式
│   ├── index.js        # 项目入口文件
│   ├── index.css       # 全局样式
│   └── ...             # 其他组件和资源
├── package.json        # 项目配置和依赖管理
├── package-lock.json   # 依赖的精确版本锁定文件
└── README.md           # 项目说明文档
```


## 核心文件解析


### public/index.html

public/index.html 是 React 应用的 HTML 模板文件。

React 会将组件渲染到 <div id="root"></div> 中。


## 实例


### src/index.js

src/index.js 负责将根组件（通常是 App）渲染到 index.html 中的 div#root 中。


## 实例


### src/App.js

src/App.js 是 React 应用的根组件。

src/App.js 通常包含应用的主要逻辑和结构。


## 实例


### src/App.css

src/App.css 是 App 组件的样式文件。


## 实例


### src/index.css

src/index.css 是全局样式文件，通常用于定义全局样式或重置浏览器默认样式。


## 实例


### package.json

package.json 这是项目的配置文件，包含项目的元数据、依赖和脚本。


## 实例


## React 组件的基本结构

React 组件是 React 应用的核心构建块。

一个组件通常包含以下部分：


### 1、函数组件

使用函数定义的组件。


## 实例

说明：

- import React from 'react';: 导入了 React 库，React 是一个用于构建用户界面的 JavaScript 库。
- function MyComponent() { ... }: 这是一个函数组件。函数组件是一个返回 JSX 的 JavaScript 函数。
- return (...): 组件的 return 语句返回一个 JSX 元素。JSX 是 JavaScript 的语法扩展，允许你在 JavaScript 中编写类似 HTML 的代码。
- export default MyComponent;: 将 MyComponent 组件导出为默认导出。这样，其他文件可以通过 import MyComponent from './MyComponent'; 来导入并使用这个组件。


### 2、类组件

使用类定义的组件（现在较少使用，推荐使用函数组件）。


## 实例

说明：

- import React from 'react';: 导入 React 库，这是使用 React 的基础。
- import { Component } from 'react';: 从 React 库中导入 Component 类。Component 是 React 类组件的基类，所有类组件都需要继承它。
- class MyComponent extends Component { ... }: 定义了一个名为 MyComponent 的类组件。它继承了 Component 类，因此可以使用 React 类组件的特性（如生命周期方法、状态管理等）。
- render() { ... }: render 是类组件中必须实现的方法。它负责返回组件的 UI 结构（JSX）。return (...): 返回一个 JSX 元素，描述组件的 UI。<div><h2>这是一个类组件</h2></div>: 这是一个简单的 JSX 结构，包含一个 div 和一个 h2 标题。
- export default MyComponent;: 将 MyComponent 组件导出为默认导出。这样，其他文件可以通过 import MyComponent from './MyComponent'; 来导入并使用这个组件。


### 3、JSX

JSX 是 JavaScript 的语法扩展，允许在 JavaScript 中编写类似 HTML 的代码。


## 实例


### 4、Props

Props 是组件的输入参数，用于从父组件向子组件传递数据。


## 实例


### 5、State

State 是组件的内部状态，用于管理组件的数据。


## 后续章节

- 实例（使用 useState Hook）
- React 项目的运行流程
- 启动开发服务器
- 构建生产环境代码
- 运行测试

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `React 项目说明` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
