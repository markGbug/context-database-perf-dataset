# Flutter：Flutter 图片与资源

- 来源：[Flutter 图片与资源](https://www.runoob.com/flutter/flutter-images.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：学习笔记
- 章节序号：3286

## 本章内容

本节将介绍 Flutter 中图片加载、本地资源管理和网络图片处理。


## Image Widget - 图片显示


## 实例：各种图片加载方式


## 本地资源管理

在 pubspec.yaml 中配置资源文件夹：

```text
flutter:
  assets:
    - assets/images/
    - assets/data.json
```


## 实例：使用本地资源


## BoxFit 图像适配


## CachedNetworkImage - 图片缓存

使用 cached_network_image 包实现图片缓存。


### 添加依赖

```text
dependencies:
  cached_network_image: ^3.0.0
```


## 实例：CachedNetworkImage

对于网络图片，建议使用 CachedNetworkImage，它可以自动缓存图片，提高加载性能。


## 复习重点

- 能说明 `Flutter 图片与资源` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
