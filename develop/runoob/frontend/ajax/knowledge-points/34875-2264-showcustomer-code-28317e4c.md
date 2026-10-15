# 知识点 34875：AJAX：AJAX 数据库 - 实例解释 - showCustomer() 函数

- 来源：[AJAX 数据库](https://www.runoob.com/ajax/ajax-database.html)
- 来源章节：[2264-ajax-database-practice.md](../chapters/2264-ajax-database-practice.md)
- 分类：前端开发
- 技术：AJAX
- 所在小节：实例解释 - showCustomer() 函数
- 知识类型：代码
- 原章节序号：2264

## 原文片段

```text
function showCustomer(str) {
    var xmlhttp;
    if (str == "") {
        document.getElementById("txtHint").innerHTML = "";
        return
    }
    if (window.XMLHttpRequest) {
        xmlhttp = new XMLHttpRequest()
    } else {
        xmlhttp = new ActiveXObject("Microsoft.XMLHTTP")
    }
    xmlhttp.onreadystatechange = function() {
        if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
            document.getElementById("txtHint").innerHTML = xmlhttp.responseText
        }
    }
    xmlhttp.open("GET", "/try/ajax/getcustomer.php?q=" + str, true);
    xmlhttp.send()
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例解释 - showCustomer() 函数` 这一小节和 `AJAX 数据库` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
