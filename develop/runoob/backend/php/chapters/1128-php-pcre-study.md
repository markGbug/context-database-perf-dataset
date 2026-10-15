# PHP：PHP 正则表达式(PCRE)

- 来源：[PHP PCRE](https://www.runoob.com/php/php-pcre.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1128

## 本章内容

正则表达式(regular expression)描述了一种字符串匹配的模式，可以用来检查一个串是否含有某种子串、将匹配的子串做替换或者从某个串中取出符合某个条件的子串等。

更多正则表达式的内容可参考我们的：正则表达式 - 教程。

PHP 中使用正则表达式主要通过一组内置的函数，其中最常用的是:

- preg_match(): 在字符串中搜索匹配的模式，只返回第一个匹配项。
- preg_match_all(): 在字符串中搜索匹配的模式，返回所有匹配项。
- preg_replace(): 在字符串中搜索匹配的模式，然后进行替换。


### preg_match() 函数

preg_match() 函数用于在字符串中搜索匹配的模式，只返回第一个匹配项。

```text
preg_match(pattern, subject, matches)
```

参数说明：

- pattern：正则表达式模式。
- subject：要搜索的字符串。
- matches：可选参数，用于存储匹配的结果。


## 实例

以上代码输出结果为：

```text
匹配成功!
Array
(
    [0] => Hello
)
```


### preg_match_all() 函数

preg_match_all() 函数用于在字符串中搜索匹配的模式，返回所有匹配项。

```text
preg_match_all(pattern, subject, matches)
```

参数说明：

- 用于在字符串中搜索匹配的模式，返回所有匹配项。
- pattern：正则表达式模式。
- subject：要搜索的字符串。
- matches：用于存储所有匹配结果的数组。


## 实例

以上代码输出结果为：

```text
匹配的元音字母: e, a, a, e, a
```


### preg_replace() 函数

preg_replace() 函数用于在字符串中搜索匹配的模式，然后进行替换。

```text
preg_replace(pattern, replacement, subject)
```

参数说明：

- pattern：正则表达式模式。
- replacement：替换的字符串。
- subject：要搜索的字符串。


## 实例

以上代码输出结果为：

```text
替换后的字符串: I love RUNOOB
```


## PCRE 函数

PHP 中我们可以使用 PCRE 扩展来匹配字符串的模式。


## PREG 常量


## 复习重点

- 能说明 `PHP PCRE` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
