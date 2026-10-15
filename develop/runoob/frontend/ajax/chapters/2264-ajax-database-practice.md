# AJAX：AJAX Database 实例

- 来源：[AJAX 数据库](https://www.runoob.com/ajax/ajax-database.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：练习笔记
- 章节序号：2264

## 本章内容

AJAX 可用来与数据库进行动态通信。


## AJAX 数据库实例

下面的例子将演示网页如何通过 AJAX 从数据库读取信息： 请在下面的下拉列表中选择一个客户：


## 实例


## 实例解释 - showCustomer() 函数

当用户在上面的下拉列表中选择某个客户时，会执行名为 "showCustomer()" 的函数。该函数由 "onchange" 事件触发：

```javascript
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

showCustomer() 函数执行以下任务：

- 检查是否已选择某个客户
- 创建 XMLHttpRequest 对象
- 当服务器响应就绪时执行所创建的函数
- 把请求发送到服务器上的文件
- 请注意我们向 URL 添加了一个参数 q （带有输入域中的内容）


## AJAX 服务器页面

由上面的 JavaScript 调用的服务器页面是 PHP 文件，名为 "getcustomer.php"。

用 PHP 编写服务器文件也很容易，或者用其他服务器语言。请看用 PHP 编写的相应的例子。

"getcustomer.php" 中的源代码负责对数据库进行查询，然后用 HTML 表格返回结果：

```html
<%
response.expires=-1
sql="SELECT * FROM CUSTOMERS WHERE CUSTOMERID="
sql=sql & "'" & request.querystring("q") & "'"

set conn=Server.CreateObject("ADODB.Connection")
conn.Provider="Microsoft.Jet.OLEDB.4.0"
conn.Open(Server.Mappath("/db/northwind.mdb"))
set rs=Server.CreateObject("ADODB.recordset")
rs.Open sql,conn

response.write("<table>")
do until rs.EOF
  for each x in rs.Fields
    response.write("<tr><td><b>" & x.name & "</b></td>")
    response.write("<td>" & x.value & "</td></tr>")
  next
  rs.MoveNext
loop
response.write("</table>")
%>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AJAX 数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
