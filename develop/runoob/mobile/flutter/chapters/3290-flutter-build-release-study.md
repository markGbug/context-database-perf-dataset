# Flutter：Flutter 打包与发布

- 来源：[Flutter 打包与发布](https://www.runoob.com/flutter/flutter-build-release.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：学习笔记
- 章节序号：3290

## 本章内容

本节将介绍如何将 Flutter 应用打包发布到各个平台。


## 构建准备

在发布前，确保应用配置正确。


### pubspec.yaml 配置


## 实例：发布配置


### Android 配置

修改 android/app/build.gradle 中的应用配置：


## 实例：Android 配置


## Android 构建


### 构建 APK

```text
# 调试 APK
$ flutter build apk --debug

# 发布 APK
$ flutter build apk --release

# 带签名（需要配置 signingConfigs）
$ flutter build apk --release --target-platform android-arm64
```


### 构建 App Bundle

```text
# 构建 App Bundle（推荐用于 Google Play）
$ flutter build appbundle --release
```


## iOS 构建


### 准备工作

- 安装 Xcode
- 配置 Apple 开发者账号
- 创建 App ID 和证书


### 命令行构建

```text
# 模拟器版本
$ flutter build ios --simulator --no-codesign

# 发布版本（需要签名）
$ flutter build ipa --release
```


### 使用 Xcode 构建

- 在 ios/ 目录打开 .xcworkspace 文件
- 选择目标设备和 Signing 配置
- 点击 Product > Archive


## Web 构建

```text
# 构建 Web 版本
$ flutter build web --release

# 输出目录：build/web/
```


### Web 配置

在 web/index.html 中配置应用：


## 实例：Web 配置


## 桌面应用构建

```text
# Windows
$ flutter build windows --release

# macOS
$ flutter build macos --release

# Linux
$ flutter build linux --release
```

发布前务必测试应用的发布版本，调试版本可能包含额外的调试信息。


## 复习重点

- 能说明 `Flutter 打包与发布` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
