# PHP：PHP 实例 - AJAX RSS 阅读器

- 来源：[AJAX RSS Reader](https://www.runoob.com/php/php-ajax-rss-reader.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1103

## 本章内容

RSS 阅读器用于阅读 RSS Feed。


## AJAX RSS 阅读器

在下面的实例中，我们将演示一个 RSS 阅读器，通过它，来自 RSS 的内容在网页不进行刷新的情况下被载入：


## 实例解释 - HTML 页面

当用户在上面的下拉列表中选择某个 RSS-feed 时，会执行名为 "showRSS()" 的函数。该函数由 "onchange" 事件触发：


## 实例

```html
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
<script>
function showRSS(str)
{
    if (str.length==0)
    {
        document.getElementById("rssOutput").innerHTML="";
        return;
        }
    if (window.XMLHttpRequest)
    {
        // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
        xmlhttp=new XMLHttpRequest();
    }
    else
    {
        // IE6, IE5 浏览器执行代码
        xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
    }
    xmlhttp.onreadystatechange=function()
    {
        if (xmlhttp.readyState==4 && xmlhttp.status==200)
        {
            document.getElementById("rssOutput").innerHTML=xmlhttp.responseText;
        }
    }
    xmlhttp.open("GET","getrss.php?q="+str,true);
    xmlhttp.send();
}
</script>
</head>
<body>

<form>
<select onchange="showRSS(this.value)">
<option value="">选择一个 RSS-feed:</option>
<option value="rss">读取 RSS 数据</option>
</select>
</form>
<br>
<div id="rssOutput">RSS-feed 数据列表...</div>
</body>
</html>
```

showRSS() 函数会执行以下步骤：

- 检查是否有 RSS-feed 被选择
- 创建 XMLHttpRequest 对象
- 创建在服务器响应就绪时执行的函数
- 向服务器上的文件发送请求
- 请注意添加到 URL 末端的参数（q）（包含下拉列表的内容）


## PHP 文件

文件 rss_demo.xml。

上面这段通过 JavaScript 调用的服务器页面是名为 "getrss.php" 的 PHP 文件：


## 实例

```java
<?php
// rss 文件
$xml="rss_demo.xml";

$xmlDoc = new DOMDocument();
$xmlDoc->load($xml);

// 从 "<channel>" 中读取元素
$channel=$xmlDoc->getElementsByTagName('channel')->item(0);
$channel_title = $channel->getElementsByTagName('title')
->item(0)->childNodes->item(0)->nodeValue;
$channel_link = $channel->getElementsByTagName('link')
->item(0)->childNodes->item(0)->nodeValue;
$channel_desc = $channel->getElementsByTagName('description')
->item(0)->childNodes->item(0)->nodeValue;

// 输出 "<channel>" 中的元素
echo("<p><a href='" . $channel_link
  . "'>" . $channel_title . "</a>");
echo("<br>");
echo($channel_desc . "</p>");

// 输出 "<item>" 中的元素
$x=$xmlDoc->getElementsByTagName('item');
for ($i=0; $i<=1; $i++) {
    $item_title=$x->item($i)->getElementsByTagName('title')
    ->item(0)->childNodes->item(0)->nodeValue;
    $item_link=$x->item($i)->getElementsByTagName('link')
    ->item(0)->childNodes->item(0)->nodeValue;
    $item_desc=$x->item($i)->getElementsByTagName('description')
    ->item(0)->childNodes->item(0)->nodeValue;
    echo ("<p><a href='" . $item_link
    . "'>" . $item_title . "</a>");
    echo ("<br>");
    echo ($item_desc . "</p>");
}
?>
```

当 RSS feed 的请求从 JavaScript 发送到 PHP 文件时，将发生：

- 检查哪个 RSS feed 被选中
- 创建一个新的 XML DOM 对象
- 在 xml 变量中加载 RSS 文档
- 从 channel 元素中提取并输出元素
- 从 item 元素中提取并输出元素


## 复习重点

- 能说明 `AJAX RSS Reader` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
