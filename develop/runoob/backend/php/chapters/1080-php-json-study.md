# PHP：PHP JSON

- 来源：[PHP JSON](https://www.runoob.com/php/php-json.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1080

## 本章内容

本章节我们将为大家介绍如何使用 PHP 语言来编码和解码 JSON 对象。


## 环境配置

在 php5.2.0 及以上版本已经内置 JSON 扩展。


## JSON 函数


## json_encode

PHP json_encode() 用于对变量进行 JSON 编码，该函数如果执行成功返回 JSON 数据，否则返回 FALSE 。


### 语法

```text
string json_encode ( $value [, $options = 0 ] )
```


### 参数

- value: 要编码的值。该函数只对 UTF-8 编码的数据有效。
- options:由以下常量组成的二进制掩码 JSON_HEX_QUOT, JSON_HEX_TAG, JSON_HEX_AMP, JSON_HEX_APOS, JSON_NUMERIC_CHECK, JSON_PRETTY_PRINT, JSON_UNESCAPED_SLASHES, JSON_FORCE_OBJECT, JSON_PRESERVE_ZERO_FRACTION, JSON_UNESCAPED_UNICODE, JSON_PARTIAL_OUTPUT_ON_ERROR。 要注意的是 JSON_UNESCAPED_UNICODE 选项，如果我们不希望中文被编码，可以添加该选项。


### 实例

以下实例演示了如何将 PHP 数组转换为 JSON 格式数据：

```text
<?php
   $arr = array('a' => 1, 'b' => 2, 'c' => 3, 'd' => 4, 'e' => 5);
   echo json_encode($arr);
?>
```

以上代码执行结果为：

```text
{"a":1,"b":2,"c":3,"d":4,"e":5}
```

以下实例演示了如何将 PHP 对象转换为 JSON 格式数据：


## 实例

以上代码执行结果为：

```text
{"name":"sachin","hobbies":"sports","birthdate":"08\/05\/1974 12:20:03 pm"}
```


## 使用 JSON_UNESCAPED_UNICODE 选项

以上代码执行结果为：

```text
{"runoob":"\u83dc\u9e1f\u6559\u7a0b","taobao":"\u6dd8\u5b9d\u7f51"}
{"runoob":"菜鸟教程","taobao":"淘宝网"}
```


## json_decode

PHP json_decode() 函数用于对 JSON 格式的字符串进行解码，并转换为 PHP 变量。


### 语法

```text
mixed json_decode ($json_string [,$assoc = false [, $depth = 512 [, $options = 0 ]]])
```


### 参数

- json_string: 待解码的 JSON 字符串，必须是 UTF-8 编码数据
- assoc: 当该参数为 TRUE 时，将返回数组，FALSE 时返回对象。
- depth: 整数类型的参数，它指定递归深度
- options: 二进制掩码，目前只支持 JSON_BIGINT_AS_STRING 。


### 实例

以下实例演示了如何解码 JSON 数据：


## 实例

以上代码执行结果为：

```text
object(stdClass)#1 (5) {
    ["a"] => int(1)
    ["b"] => int(2)
    ["c"] => int(3)
    ["d"] => int(4)
    ["e"] => int(5)
}

array(5) {
    ["a"] => int(1)
    ["b"] => int(2)
    ["c"] => int(3)
    ["d"] => int(4)
    ["e"] => int(5)
}
```


## 复习重点

- 能说明 `PHP JSON` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
