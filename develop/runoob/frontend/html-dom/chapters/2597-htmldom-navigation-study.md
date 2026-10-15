# HTML DOM：HTML DOM 导航

- 来源：[HTML DOM 导航](https://www.runoob.com/htmldom/htmldom-navigation.html)
- 分类：前端开发
- 技术：HTML DOM
- 笔记类型：学习笔记
- 章节序号：2597

## 本章内容

通过 HTML DOM，您能够使用节点关系在节点树中导航。


## HTML DOM 节点列表

getElementsByTagName() 方法返回节点列表。节点列表是一个节点数组。

下面的代码选取文档中的所有 <p> 节点：


## 实例

```javascript
var x=document.getElementsByTagName("p");
```

可以通过下标号访问这些节点。如需访问第二个 <p>，您可以这么写：

```text
y=x[1];
```


## 复习重点

- 能说明 `HTML DOM 导航` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
