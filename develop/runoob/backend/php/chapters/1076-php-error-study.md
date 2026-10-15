# PHP：PHP 错误处理

- 来源：[PHP Error](https://www.runoob.com/php/php-error.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1076

## 本章内容

在 PHP 中，默认的错误处理很简单。一条错误消息会被发送到浏览器，这条消息带有文件名、行号以及描述错误的消息。


## PHP 错误处理

在创建脚本和 Web 应用程序时，错误处理是一个重要的部分。如果您的代码缺少错误检测编码，那么程序看上去很不专业，也为安全风险敞开了大门。

本教程介绍了 PHP 中一些最为重要的错误检测方法。

我们将为您讲解不同的错误处理方法：

- 简单的 "die()" 语句
- 自定义错误和错误触发器
- 错误报告


## 基本的错误处理：使用 die() 函数

第一个实例展示了一个打开文本文件的简单脚本：

```text
<?php
$file=fopen("welcome.txt","r");
?>
```

如果文件不存在，您会得到类似这样的错误：

```text
Warning: fopen(welcome.txt) [function.fopen]: failed to open stream:
No such file or directory in /www/runoob/test/test.php on line 2
```

为了避免用户得到类似上面的错误消息，我们在访问文件之前检测该文件是否存在：

```text
<?php
if(!file_exists("welcome.txt"))
{
    die("文件不存在");
}
else
{
    $file=fopen("welcome.txt","r");
}
?>
```

现在，如果文件不存在，您会得到类似这样的错误消息：

```text
文件不存在
```

相比之前的代码，上面的代码更有效，这是由于它采用了一个简单的错误处理机制在错误之后终止了脚本。

然而，简单地终止脚本并不总是恰当的方式。让我们研究一下用于处理错误的备选的 PHP 函数。


## 创建自定义错误处理器

创建一个自定义的错误处理器非常简单。我们很简单地创建了一个专用函数，可以在 PHP 中发生错误时调用该函数。

该函数必须有能力处理至少两个参数 (error level 和 error message)，但是可以接受最多五个参数（可选的：file, line-number 和 error context）：


## 语法

```text
error_function(error_level,error_message,
error_file,error_line,error_context)
```


## 错误报告级别

这些错误报告级别是用户自定义的错误处理程序处理的不同类型的错误：

现在，让我们创建一个处理错误的函数：

```html
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr<br>";
    echo "脚本结束";
    die();
}
```

上面的代码是一个简单的错误处理函数。当它被触发时，它会取得错误级别和错误消息。然后它会输出错误级别和消息，并终止脚本。

现在，我们已经创建了一个错误处理函数，我们需要确定在何时触发该函数。


## 设置错误处理程序

PHP 的默认错误处理程序是内建的错误处理程序。我们打算把上面的函数改造为脚本运行期间的默认错误处理程序。

可以修改错误处理程序，使其仅应用到某些错误，这样脚本就能以不同的方式来处理不同的错误。然而，在本例中，我们打算针对所有错误来使用我们自定义的错误处理程序：

```text
set_error_handler("customError");
```

由于我们希望我们的自定义函数能处理所有错误，set_error_handler() 仅需要一个参数，可以添加第二个参数来规定错误级别。


## 实例

通过尝试输出不存在的变量，来测试这个错误处理程序：

```html
<?php
// 错误处理函数
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr";
}

// 设置错误处理函数
set_error_handler("customError");

// 触发错误
echo($test);
?>
```

以上代码的输出如下所示：

```text
Error: [8] Undefined variable: test
```


## 触发错误

在脚本中用户输入数据的位置，当用户的输入无效时触发错误是很有用的。在 PHP 中，这个任务由 trigger_error() 函数完成。


## 实例

在本例中，如果 "test" 变量大于 "1"，就会发生错误：

```text
<?php
$test=2;
if ($test>1)
{
    trigger_error("变量值必须小于等于 1");
}
?>
```

以上代码的输出如下所示：

```text
Notice: 变量值必须小于等于 1
in /www/test/runoob.php on line 5
```

您可以在脚本中任何位置触发错误，通过添加的第二个参数，您能够规定所触发的错误类型。

可能的错误类型：

- E_USER_ERROR - 致命的用户生成的 run-time 错误。错误无法恢复。脚本执行被中断。
- E_USER_WARNING - 非致命的用户生成的 run-time 警告。脚本执行不被中断。
- E_USER_NOTICE - 默认。用户生成的 run-time 通知。在脚本发现可能有错误时发生，但也可能在脚本正常运行时发生。


## 实例

在本例中，如果 "test" 变量大于 "1"，则发生 E_USER_WARNING 错误。如果发生了 E_USER_WARNING，我们将使用我们自定义的错误处理程序并结束脚本：

```html
<?php
// 错误处理函数
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr<br>";
    echo "脚本结束";
    die();
}

// 设置错误处理函数
set_error_handler("customError",E_USER_WARNING);

// 触发错误
$test=2;
if ($test>1)
{
    trigger_error("变量值必须小于等于 1",E_USER_WARNING);
}
?>
```

以上代码的输出如下所示：

```text
Error: [512] 变量值必须小于等于 1
脚本结束
```

现在，我们已经学习了如何创建自己的 error，以及如何触发它们，接下来我们研究一下错误记录。


## 错误记录

在默认的情况下，根据在 php.ini 中的 error_log 配置，PHP 向服务器的记录系统或文件发送错误记录。通过使用 error_log() 函数，您可以向指定的文件或远程目的地发送错误记录。

通过电子邮件向您自己发送错误消息，是一种获得指定错误的通知的好办法。


## 通过 E-Mail 发送错误消息

在下面的例子中，如果特定的错误发生，我们将发送带有错误消息的电子邮件，并结束脚本：

```html
<?php
// 错误处理函数
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr<br>";
    echo "已通知网站管理员";
    error_log("Error: [$errno] $errstr",1,
    "someone@example.com","From: webmaster@example.com");
}

// 设置错误处理函数
set_error_handler("customError",E_USER_WARNING);

// 触发错误
$test=2;
if ($test>1)
{
    trigger_error("变量值必须小于等于 1",E_USER_WARNING);
}
?>
```

以上代码的输出如下所示：

```text
Error: [512] 变量值必须小于等于 1
已通知网站管理员
```

接收自以上代码的邮件如下所示：

```text
Error: [512] 变量值必须小于等于 1
```

这个方法不适合所有的错误。常规错误应当通过使用默认的 PHP 记录系统在服务器上进行记录。


## 复习重点

- 能说明 `PHP Error` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
