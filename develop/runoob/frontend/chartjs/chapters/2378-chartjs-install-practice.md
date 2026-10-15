# Chart.js：Chart.js 安装

- 来源：[Chart.js 安装](https://www.runoob.com/chartjs/chartjs-install.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：练习笔记
- 章节序号：2378

## 本章内容

Chart.js 提供了多种安装方式，适合不同的开发场景：

- NPM/Yarn - 适合使用构建工具的项目开发
- CDN - 适合快速原型开发和学习
- GitHub - 适合需要最新特性或参与贡献的开发


## 1. 通过 NPM/Yarn 安装

NPM (Node Package Manager) 是 JavaScript 的包管理工具，适合现代前端项目开发。


### 安装步骤

```text
# 使用 npm 安装
npm install chart.js

# 或者使用 yarn 安装
yarn add chart.js
```


### 在项目中引入

安装完成后，你可以在 JavaScript 文件中这样引入 Chart.js：


## 实例


### 版本管理

要安装特定版本的 Chart.js，可以指定版本号：

```text
npm install chart.js@3.9.1
```


## 2. 通过 CDN 使用

CDN (Content Delivery Network) 是通过网络直接加载库文件的方式，适合快速原型开发。


### 推荐 CDN 地址

```html
<!-- 字节跳动 CDN（国内推荐） -->
<script src="<script src="https://lf6-cdn-tos.bytecdntp.com/cdn/expire-1-M/Chart.js/3.7.1/chart.min.js"></script>"></script>

<!-- Staticfile CDN（国内备选） -->
<script src="https://cdn.staticfile.net/Chart.js/3.9.1/chart.min.js"></script>

<!-- cdnjs CDN（海外推荐） -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
```


## 实例

本系列会采用国内的 CDN 地址来测试，如下实例：


## 实例


## 3. 从 GitHub 获取

GitHub 是开源项目的托管平台，适合需要最新特性或参与项目贡献的开发者。


### 获取方式

克隆仓库（需要 Git）：

```text
git clone https://github.com/chartjs/Chart.js.git
```


### 下载 ZIP 文件

- 访问 Chart.js GitHub
- 点击 "Code" 按钮
- 选择 "Download ZIP"


### 构建项目

下载后，你可以构建自己的 Chart.js 版本：

```text
cd Chart.js
npm install
npm run build
```

构建完成后，可以在 dist/ 目录找到生成的文件。


## 安装方式对比


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Chart.js 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
