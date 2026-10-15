# jQuery EasyUI：jQuery EasyUI 简介

- 来源：[jQuery EasyUI 简介](https://www.runoob.com/jeasyui/jqueryeasyui-intro.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2841

## 本章内容

jQuery EasyUI 是一个基于 jQuery 的框架，集成了各种用户界面插件。


## 什么是 jQuery EasyUI

jQuery EasyUI 框架提供了创建网页所需的一切，帮助您轻松建立站点。

- easyui 是一个基于 jQuery 的框架，集成了各种用户界面插件。
- easyui 提供建立现代化的具有交互性的 javascript 应用的必要的功能。
- 使用 easyui，您不需要写太多 javascript 代码，一般情况下您只需要使用一些 html 标记来定义用户界面。
- HTML 网页的完整框架。
- easyui 节省了开发产品的时间和规模。
- easyui 非常简单，但是功能非常强大。


## jQuery EasyUI 下载

您可以从 http://www.jeasyui.com/download/index.php 上下载您需要的 jQuery EasyUI 版本。


## 轻松使用 jQuery 和 HTML5

jQuery EasyUI 提供易于使用的组件，它使 Web 开发人员快速地在流行的 jQuery 核心和 HTML5 上建立程序页面。 这些功能使您的应用适合今天的网络。 有两个方法声明的 UI 组件:

1. 直接在 HTML 声明组件。

```html
<div class="easyui-dialog" style="width:400px;height:200px"
    data-options="title:'My Dialog',collapsible:true,iconCls:'icon-ok',onOpen:function(){}">
        dialog content.
</div>
```

2. 编写 JavaScript 代码来创建组件。

```html
<input id="cc" style="width:200px" />
```

```text
$('#cc').combobox({
    url: ...,
    required: true,
    valueField: 'id',
    textField: 'text'
});
```


## 复习重点

- 能说明 `jQuery EasyUI 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
