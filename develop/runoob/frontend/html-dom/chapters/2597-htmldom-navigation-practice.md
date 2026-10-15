# HTML DOM：HTML DOM 导航

- 来源：[HTML DOM 导航](https://www.runoob.com/htmldom/htmldom-navigation.html)
- 分类：前端开发
- 技术：HTML DOM
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML DOM 导航` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
