# jQuery：jQuery Accordion

- 来源：[jQuery Accordion](https://www.runoob.com/jquery/jquery-plugin-accordion.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：3003

## 本章内容

jQuery Accordion 插件用于创建折叠菜单。它通常与嵌套的列表、定义列表或嵌套的 div 一起使用。选项用于指定结构、激活的元素和定制的动画。

该插件现在是 jQuery UI 的一部分，独立的版本不会再更新了。目前版本是 1.6。

jQuery Accordion 官网，jQuery Accordion 插件下载：http://www.runoob.com/try/download/jquery-accordion.zip。

如需了解更多有关 Accordion 的细节，请查看 API 文档 折叠面板部件（Accordion Widget）。


## 标准

标准代码如下:

```text
jQuery('#list1a').accordion();
jQuery('#list1b').accordion({
    autoheight: false
});
```


## 导航

带有锚和嵌套列表的无序列表

```text
jQuery('#navigation').accordion({
    active: false,
    header: '.head',
    navigation: true,
    event: 'mouseover',
    fillSpace: true,
    animated: 'easeslide'
});
```


## 带选项

容器是一个定义列表，标题是 dt，内容是 dd。

```html
jQuery('#list2').accordion({
    event: 'mouseover',
    active: '.selected',
    selectedClass: 'active',
    animated: "bounceslide",
    header: "dt"
}).bind("change.ui-accordion", function(event, ui) {
    jQuery('<div>' + ui.oldHeader.text() + ' hidden, ' + ui.newHeader.text() + ' shown</div>').appendTo('#log');
});
```

查看演示 源码下载


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Accordion` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
