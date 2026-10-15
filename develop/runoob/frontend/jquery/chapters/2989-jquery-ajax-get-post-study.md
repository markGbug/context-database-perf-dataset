# jQuery：jQuery - AJAX get() 和 post() 方法

- 来源：[jQuery get()/post() 方法](https://www.runoob.com/jquery/jquery-ajax-get-post.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：2989

## 本章内容

jQuery get() 和 post() 方法用于通过 HTTP GET 或 POST 请求从服务器请求数据。


## HTTP 请求：GET vs POST

两种在客户端和服务器端进行请求-响应的常用方法是：GET 和 POST。

- GET - 从指定的资源请求数据
- POST - 向指定的资源提交要处理的数据

GET 基本上用于从服务器获得（取回）数据。注释：GET 方法可能返回缓存数据。

POST 也可用于从服务器获取数据。不过，POST 方法不会缓存数据，并且常用于连同请求一起发送数据。

如需学习更多有关 GET 和 POST 以及两方法差异的知识，请阅读我们的 HTTP 方法 - GET 对比 POST。


## jQuery $.get() 方法

$.get() 方法通过 HTTP GET 请求从服务器上请求数据。


### 语法：

```text
$.get(URL,callback);
或
$.get( URL [, data ] [, callback ] [, dataType ] )
```

- URL：发送请求的 URL字符串。
- data：可选的，发送给服务器的字符串或 key/value 键值对。
- callback：可选的，请求成功后执行的回调函数。
- dataType：可选的，从服务器返回的数据类型。默认：智能猜测（可以是xml, json, script, 或 html）。

下面的例子使用 $.get() 方法从服务器上的一个文件中取回数据：


## 实例

```text
$("button").click(function(){
  $.get("demo_test.php",function(data,status){
    alert("数据: " + data + "\n状态: " + status);
  });
});
```

$.get() 的第一个参数是我们希望请求的 URL（"demo_test.php"）。

第二个参数是回调函数。第一个回调参数存有被请求页面的内容，第二个回调参数存有请求的状态。

提示： 这个 PHP 文件 ("demo_test.php") 类似这样：


## demo_test.php 文件代码:

```text
<?php
echo '这是个从PHP文件中读取的数据。';
?>
```


## jQuery $.post() 方法

$.post() 方法通过 HTTP POST 请求向服务器提交数据。

语法:

```text
$.post(URL,callback);
或
$.post( URL [, data ] [, callback ] [, dataType ] )
```

- URL：发送请求的 URL字符串。
- data：可选的，发送给服务器的字符串或 key/value 键值对。
- callback：可选的，请求成功后执行的回调函数。
- dataType：可选的，从服务器返回的数据类型。默认：智能猜测（可以是xml, json, script, 或 html）。

下面的例子使用 $.post() 连同请求一起发送数据：


## 实例

```text
$("button").click(function(){
    $.post("/try/ajax/demo_test_post.php",
    {
        name:"菜鸟教程",
        url:"http://www.runoob.com"
    },
    function(data,status){
        alert("数据: \n" + data + "\n状态: " + status);
    });
});
```

$.post() 的第一个参数是我们希望请求的 URL ("demo_test_post.php")。

然后我们连同请求（name 和 url）一起发送数据。

"demo_test_post.php" 中的 PHP 脚本读取这些参数，对它们进行处理，然后返回结果。

第三个参数是回调函数。第一个回调参数存有被请求页面的内容，而第二个参数存有请求的状态。

提示： 这个 PHP 文件 ("demo_test_post.php") 类似这样：


## demo_test_post.php 文件代码:

```text
<?php
$name = isset($_POST['name']) ? htmlspecialchars($_POST['name']) : '';
$url = isset($_POST['url']) ? htmlspecialchars($_POST['url']) : '';
echo '网站名: ' . $name;
echo "\n";
echo 'URL 地址: ' .$url;
?>
```


## 复习重点

- 能说明 `jQuery get()/post() 方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
