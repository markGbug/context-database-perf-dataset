# Flutter：Flutter 项目结构

- 来源：[Flutter 项目结构](https://www.runoob.com/flutter/flutter-project-structure.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：学习笔记
- 章节序号：3272

## 本章内容

了解 Flutter 项目的目录结构对于高效开发至关重要。

本节将详细介绍 Flutter 项目的各个组成部分及其作用。


## 项目目录结构

当你使用 flutter create 创建新项目后，会得到以下目录结构：

```text
my_app/
├── android/          # Android 平台相关代码
├── ios/              # iOS 平台相关代码
├── lib/              # Dart 代码目录（主要开发目录）
│   └── main.dart     # 应用入口文件
├── web/              # Web 平台相关代码
├── windows/          # Windows 桌面相关代码
├── macos/            # macOS 桌面相关代码
├── linux/            # Linux 桌面相关代码
├── test/             # 测试代码目录
├── pubspec.yaml      # 项目配置文件
├── pubspec.lock      # 依赖锁定文件（自动生成）
├── analysis_options.yaml  # Dart 分析器配置
└── README.md         # 项目说明文件
```


## 主要目录和文件说明


### lib/ 目录 - 核心代码目录

lib/ 目录是你编写 Dart 代码的主要地方。所有应用逻辑都应该放在这里。


### android/ 目录 - Android 平台

包含 Android 原生项目文件，用于：

- 配置应用名称和图标
- 设置应用权限
- 集成原生 SDK（如 Google Play 服务）


### ios/ 目录 - iOS 平台

包含 iOS 原生项目文件（Xcode 项目），用于：

- 配置应用名称和图标
- 设置 iOS 特有的配置
- 集成 CocoaPods 依赖


### test/ 目录 - 测试代码

包含应用的测试代码，通常包括：

- 单元测试
- Widget 测试
- 集成测试


### pubspec.yaml - 项目配置

pubspec.yaml 是 Flutter 项目的核心配置文件，定义项目名称、版本、依赖等。


## 实例：pubspec.yaml 示例


### pubspec.yaml 常用字段


## 依赖管理


### 添加依赖

使用 flutter pub add 命令添加依赖：

```text
$ flutter pub add http
```

或者手动编辑 pubspec.yaml 后运行：

```text
$ flutter pub get
```


### 常用依赖命令


## 推荐的项目结构

随着应用规模增大，建议采用清晰的项目结构：

```text
lib/
├── main.dart              # 入口文件
├── app.dart               # 应用配置
├── core/                  # 核心功能
│   ├── constants/         # 常量定义
│   ├── theme/             # 主题配置
│   └── utils/             # 工具类
├── data/                  # 数据层
│   ├── models/            # 数据模型
│   ├── repositories/     # 仓库（数据接口）
│   └── services/          # 网络服务
├── domain/                # 领域层
│   └── entities/          # 实体类
├── presentation/          # 展示层
│   ├── pages/             # 页面
│   ├── widgets/           # 组件
│   └── providers/         # 状态管理
└── routes/                # 路由配置
```

良好的项目结构可以提高代码可维护性，建议根据应用规模选择合适的结构。


## 复习重点

- 能说明 `Flutter 项目结构` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
