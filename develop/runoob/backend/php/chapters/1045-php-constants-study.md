# PHP：PHP 常量

- 来源：[PHP 常量](https://www.runoob.com/php/php-constants.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1045

## 本章内容

PHP 中的常量是指一旦定义后其值不能被改变的标识符。

常量值被定义后，在脚本的其他任何地方都不能被改变。

常量可以用 define() 函数或 const 关键字来定义。


### 常量的特性


## PHP 常量

- 不变性: 常量一旦定义，其值不能改变。
- 全局作用域: 常量在定义后，可以在整个脚本的任何地方使用，无需使用 global 关键字。
- 数据类型: 常量的值可以是标量数据类型（如布尔值、整数、浮点数、字符串）或数组（PHP 7 及以上版本）。
- 区分大小写: 常量名称默认是区分大小写的。如果需要定义大小写不敏感的常量，可以在 define() 函数的第三个参数设置为 true。

常量是一个简单值的标识符，该值在脚本中不能改变。

一个常量由英文字母、下划线、和数字组成，但数字不能作为首字母出现。 (常量名不需要加 $ 修饰符)。

注意： 常量在整个脚本中都可以使用。


## 设置 PHP 常量

设置常量，使用 define() 函数，函数语法如下：

```text
bool define ( string $name , mixed $value [, bool $case_insensitive = false ] )
```

该函数有三个参数:

- name：必选参数，常量名称，即标志符。
- value：必选参数，常量的值。
- case_insensitive ：可选参数，如果设置为 TRUE，该常量则大小写不敏感，默认是大小写敏感的。注意：自 PHP 7.3.0 开始，定义不区分大小写的常量已被弃用。从 PHP 8.0.0 开始，只有 false 是可接受的值，传递 true 将产生一个警告。

以下实例我们创建一个 区分大小写的常量（PHP7.3 版本之后不建议使用）, 常量值为 "欢迎访问 Runoob.com"：


## 实例

```html
<?php
// 区分大小写的常量名
define("GREETING", "欢迎访问 Runoob.com");
echo GREETING;    // 输出 "欢迎访问 Runoob.com"
echo '<br>';
echo greeting;   // 输出 "greeting"，但是有警告信息，表示该常量未定义
?>
```

以下实例我们创建一个 不区分大小写的常量, 常量值为 "欢迎访问 Runoob.com"：


## 实例

```text
<?php
// 不区分大小写的常量名
define("GREETING", "欢迎访问 Runoob.com", true);
echo greeting;  // 输出 "欢迎访问 Runoob.com"
?>
```


## 常量是全局的

常量在定义后，默认是全局变量，可以在整个运行的脚本的任何地方使用。

以下实例演示了在函数内使用常量，即便常量定义在函数外也可以正常使用常量。


## 实例

```javascript
<?php
define("GREETING", "欢迎访问 Runoob.com");

function myTest() {
    echo GREETING;
}

myTest();    // 输出 "欢迎访问 Runoob.com"
?>
```


## 使用 const 关键字

```javascript
const CONSTANT_NAME = "value";
```

以下是一个使用 const 关键字定义常量的实例：


## 实例


## 预定义常量

PHP 提供了一些预定义常量，可以在脚本中直接使用。这些常量通常用于获取 PHP 的配置信息、版本信息等。常见的预定义常量有：

- PHP_VERSION：当前 PHP 解析器的版本。
- PHP_OS：服务器的操作系统。
- PHP_INT_MAX：最大的整数值。
- E_ERROR、E_WARNING、E_PARSE 等：错误报告级别。


## 实例


## 常量数组（PHP 7 及以上版本）

在 PHP 7 及以上版本中，常量也可以是数组。


## 实例

或者使用 const：


## 实例


## 复习重点

- 能说明 `PHP 常量` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
