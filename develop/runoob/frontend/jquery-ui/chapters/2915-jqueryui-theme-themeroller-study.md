# jQuery UI：jQuery UI ThemeRoller

- 来源：[jQuery UI ThemeRoller](https://www.runoob.com/jqueryui/jqueryui-theme-themeroller.html)
- 分类：前端开发
- 技术：jQuery UI
- 笔记类型：学习笔记
- 章节序号：2915

## 本章内容

### ThemeRoller 简介

ThemeRoller 是一个 Web 应用程序，为 jQuery UI 设计和下载自定义主题提供了直观的界面。您可以访问 jQuery UI ThemeRoller 进行主题定制。

jQuery UI ThemeRoller 是由波士顿的 Filament Group, Inc 设计和开发的。


### ThemeRoller 界面

ThemeRoller 的界面分为不同面板，各面板分别是全局字体和圆角半径设置、小部件容器样式、可点击元素的互动状态，及覆盖和阴影的各种样式。这些面板允许配置各种 CSS 属性，比如字体尺寸、颜色、粗细、背景颜色和纹理、边框颜色、文本颜色、图标颜色、圆角半径，等等。


### 主题馆（Gallery）：预先设计主题

ThemeRoller 主题可以通过永久链接 URL 进行查看，它包含一些预先设计的主题可供选择。主题馆（Gallery）可以通过位于应用程序界面顶端的标签栏进行访问。从主题馆（Gallery）中，您可以预览和下载主题，甚至可以选择一个主题，然后切换到 "Roll Your Own" 标签页进行调整。


### 下载主题

当您设计完主题后，您可以下载主题以便在项目中进行使用。ThemeRoller 在顶部有一个 "Download theme（下载主题）" 按钮，可以生成一个 zip 压缩包，包含了所有的主题相关文件。下载文件中的图像是按照您的规格进行生成的，并保存为高质量的 PNG 文件。

您的主题将包含图像和 CSS，组成了 jQuery UI CSS 框架的自定义版本，包含了所有插件的图像和 CSS。


### 在项目中按照下载的主题

一旦下载了主题，解压缩后，您将看到一个名为 themes 的文件夹。该文件夹包括了主题所需的 CSS 和图像。复制主题文件夹到您的项目中，并在页面中链接 themes/all.css 文件。


### 创建自定义的 "ThemeRoller-Ready" 组件

ThemeRoller 生成了一个 jQuery UI CSS 框架的自定义版本，用于开发您自己的 ThemeRoller-ready jQuery 组件。通过这个框架生成的类被设计来提供通用的用户界面的设计情况，包括状态、图标以及各种辅助类。

如需了解更多 jQuery UI CSS 框架的开发信息，请查看 主题化 API 文档。


## 复习重点

- 能说明 `jQuery UI ThemeRoller` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
