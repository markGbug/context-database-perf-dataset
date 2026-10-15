# Flutter：Flutter 图片与资源

- 来源：[Flutter 图片与资源](https://www.runoob.com/flutter/flutter-images.html)
- 分类：移动开发
- 技术：Flutter
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flutter 图片与资源` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
