# Linux：Shell 流程控制

- 来源：[Shell 流程控制](https://www.runoob.com/linux/linux-shell-process-control.html)
- 分类：后端开发
- 技术：Linux
- 笔记类型：学习笔记
- 章节序号：0990

## 本章内容

和 Java、PHP 等语言不一样，sh 的流程控制不可为空，如(以下为 PHP 流程控制写法)：


## 实例

在 sh/bash 里可不能这么写，如果 else 分支没有语句执行，就不要写这个 else。


## if else


### if

if 语句语法格式：

```text
if condition
then
    command1
    command2
    ...
    commandN
fi
```

写成一行（适用于终端命令提示符）：

```text
if [ $(ps -ef | grep -c "ssh") -gt 1 ]; then echo "true"; fi
```

末尾的 fi 就是 if 倒过来拼写，后面还会遇到类似的。


### if else

if else 语法格式：

```text
if condition
then
    command1
    command2
    ...
    commandN
else
    command
fi
```


### if else-if else

if else-if else 语法格式：

```text
if condition1
then
    command1
elif condition2
then
    command2
else
    commandN
fi
```

if else 的 [...] 判断语句中大于使用 -gt，小于使用 -lt。

```text
if [ "$a" -gt "$b" ]; then
    ...
fi
```

如果使用 ((...)) 作为判断语句，大于和小于可以直接使用 > 和 <。

```text
if (( a > b )); then
    ...
fi
```

以下实例判断两个变量是否相等：


## 实例

输出结果：

```text
a 小于 b
```

使用 ((...)) 作为判断语句:


## 实例

输出结果：

```text
a 小于 b
```

if else 语句经常与 test 命令结合使用，如下所示：


## 实例

输出结果：

```text
两个数字相等!
```


## for 循环

与其他编程语言类似，Shell支持for循环。

for循环一般格式为：

```javascript
for var in item1 item2 ... itemN
do
    command1
    command2
    ...
    commandN
done
```

写成一行：

```javascript
for var in item1 item2 ... itemN; do command1; command2… done;
```

当变量值在列表里，for 循环即执行一次所有命令，使用变量名获取列表中的当前取值。命令可为任何有效的 shell 命令和语句。in 列表可以包含替换、字符串和文件名。

in列表是可选的，如果不用它，for循环使用命令行的位置参数。

例如，顺序输出当前列表中的数字：


## 实例

输出结果：

```text
The value is: 1
The value is: 2
The value is: 3
The value is: 4
The value is: 5
```

顺序输出字符串中的字符：

```text
#!/bin/bash

for str in This is a string
do
    echo $str
done
```

输出结果：

```text
This
is
a
string
```


## while 语句

while 循环用于不断执行一系列命令，也用于从输入文件中读取数据。其语法格式为：

```java
while condition
do
    command
done
```

以下是一个基本的 while 循环，测试条件是：如果 int 小于等于 5，那么条件返回真。int 从 1 开始，每次循环处理时，int 加 1。运行上述脚本，返回数字 1 到 5，然后终止。


## 实例

运行脚本，输出：

```text
1
2
3
4
5
```

以上实例使用了 Bash let 命令，它用于执行一个或多个表达式，变量计算中不需要加上 $ 来表示变量，具体可查阅：Bash let 命令

while循环可用于读取键盘信息。下面的例子中，输入信息被设置为变量FILM，按<Ctrl-D>结束循环。


## 实例

运行脚本，输出类似下面：

```html
按下 <CTRL-D> 退出
输入你最喜欢的网站名:菜鸟教程
是的！菜鸟教程 是一个好网站
```


### 无限循环

无限循环语法格式：

```java
while :
do
    command
done
```

或者

```java
while true
do
    command
done
```

或者

```java
for (( ; ; ))
```


## 复习重点

- 能说明 `Shell 流程控制` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
