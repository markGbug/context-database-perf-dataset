# jQuery：jQuery - 获取内容和属性

- 来源：[jQuery 捕获](https://www.runoob.com/jquery/jquery-dom-get.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2975

## 本章内容

jQuery 拥有可操作 HTML 元素和属性的强大方法。


## jQuery DOM 操作

jQuery 中非常重要的部分，就是操作 DOM 的能力。

jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。

DOM 定义访问 HTML 和 XML 文档的标准：

"W3C 文档对象模型独立于平台和语言的界面，允许程序和脚本动态访问和更新文档的内容、结构以及样式。"


## 获得内容 - text()、html() 以及 val()

三个简单实用的用于 DOM 操作的 jQuery 方法：

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括 HTML 标签）
- val() - 设置或返回表单字段的值

下面的例子演示如何通过 jQuery text() 和 html() 方法来获得内容：


## 实例

```text
$("#btn1").click(function(){
  alert("Text: " + $("#test").text());
});
$("#btn2").click(function(){
  alert("HTML: " + $("#test").html());
});
```

下面的例子演示如何通过 jQuery val() 方法获得输入字段的值：


## 实例

```text
$("#btn1").click(function(){
  alert("值为: " + $("#test").val());
});
```


## 获取属性 - attr()

jQuery attr() 方法用于获取属性值。

下面的例子演示如何获得链接中 href 属性的值：


## 实例

```text
$("button").click(function(){
  alert($("#runoob").attr("href"));
});
```

下一章会讲解如何设置（改变）内容和属性值。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 捕获` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
