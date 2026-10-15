# XML DOM：XML DOM 遍历节点树

- 来源：[DOM 遍历](https://www.runoob.com/dom/dom-nodes-traverse.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4382

## 本章内容

遍历（Traverse）意味着在节点树中进行循环或移动。


## 遍历节点树

通常您想要循环 XML 文档，比如：当您需要提取每个元素的值时。

这叫做"遍历节点树"。

下面的实例遍历 <book> 的所有子节点，并显示他们的名称和值：


## 实例

```html
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
```

```java
var x, i ,xmlDoc;
var txt = "";
var text = "<book>" +
"<title>Everyday Italian</title>" +
"<author>Giada De Laurentiis</author>" +
"<year>2005</year>" +
"</book>";

parser = new DOMParser();
xmlDoc = parser.parseFromString(text,"text/xml");

// documentElement 表示根节点
x = xmlDoc.documentElement.childNodes;
for (i = 0; i < x.length ;i++) {
    txt += x[i].nodeName + ": " + x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("demo").innerHTML = txt;
```

```text
</script>

</body>
</html>
```

输出：

实例解释：

- 将 XML 字符串载入 xmlDoc 中
- 获取根元素的子节点
- 输出每个子节点的节点名称以及文本节点的节点值


## 复习重点

- 能说明 `DOM 遍历` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
