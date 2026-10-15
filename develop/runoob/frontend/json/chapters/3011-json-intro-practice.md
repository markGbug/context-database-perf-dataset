# JSON：JSON - 简介

- 来源：[JSON 简介](https://www.runoob.com/json/json-intro.html)
- 分类：前端开发
- 技术：JSON
- 笔记类型：练习笔记
- 章节序号：3011

## 本章内容

## 在线实例

通过我们的编辑器，您可以在线编辑 JavaScript 代码，然后通过点击一个按钮来查看结果：


## JSON 实例

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<h2>JavaScript 创建 JSON 对象</h2>
<p>
网站名称: <span id="jname"></span><br />
网站地址: <span id="jurl"></span><br />
网站 slogan: <span id="jslogan"></span><br />
</p>
<script>
```

```javascript
var JSONObject= {
    "name":"菜鸟教程",
    "url":"www.runoob.com",
    "slogan":"学的不仅是技术，更是梦想！"
};
document.getElementById("jname").innerHTML=JSONObject.name
document.getElementById("jurl").innerHTML=JSONObject.url
document.getElementById("jslogan").innerHTML=JSONObject.slogan
```

```text
</script>

</body>
</html>
```


## 与 XML 相同之处

- JSON 是纯文本
- JSON 具有"自我描述性"（人类可读）
- JSON 具有层级结构（值中存在值）
- JSON 可通过 JavaScript 进行解析
- JSON 数据可使用 AJAX 进行传输


## 与 XML 不同之处

- 没有结束标签
- 更短
- 读写的速度更快
- 能够使用内建的 JavaScript eval() 方法进行解析
- 使用数组
- 不使用保留字


## 为什么使用 JSON？

对于 AJAX 应用程序来说，JSON 比 XML 更快更易使用：

- 读取 XML 文档
- 使用 XML DOM 来循环遍历文档
- 读取值并存储在变量中
- 读取 JSON 字符串
- 用 eval() 处理 JSON 字符串


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JSON 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
