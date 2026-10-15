# PHP：PHP 运算符

- 来源：[PHP 运算符](https://www.runoob.com/php/php-operators.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1047

## 本章内容

本章节我们将讨论 PHP 中不同运算符的应用。

在 PHP 中，赋值运算符 = 用于给变量赋值。

在 PHP 中，算术运算符 + 用于把值加在一起。


## PHP 算术运算符

```text
<?php
$x = 2;
echo -$x;
?>
```

x 取反，按二进制位进行"取反"运算。运算规则：

```text
~1=-2;
~0=-1;
```

```text
<?php
$x = 2;
echo ~$x;
?>
```

以下实例演示了使用不同算术运算符得到的不同结果：


## 实例

```html
<?php
$x=10;
$y=6;
echo ($x + $y); // 输出16
echo '<br>';  // 换行

echo ($x - $y); // 输出4
echo '<br>';  // 换行

echo ($x * $y); // 输出60
echo '<br>';  // 换行

echo ($x / $y); // 输出1.6666666666667
echo '<br>';  // 换行

echo ($x % $y); // 输出4
echo '<br>';  // 换行

echo -$x;
?>
```

PHP7+ 版本新增整除运算符 intdiv()，该函数返回值为第一个参数除于第二个参数的值并取整（向下取整），使用实例：


## 实例

```text
<?php
var_dump(intdiv(10, 3));
?>
```

以上实例会输出：

```text
int(3)
```


## PHP 赋值运算符

在 PHP 中，基本的赋值运算符是 =。它意味着左操作数被设置为右侧表达式的值。也就是说，$x = 5 的值是 5。

以下实例演示了使用不同赋值运算符得到的不同结果：


## 实例

```text
<?php
$x=10;
echo $x; // 输出10

$y=20;
$y += 100;
echo $y; // 输出120

$z=50;
$z -= 25;
echo $z; // 输出25

$i=5;
$i *= 6;
echo $i; // 输出30

$j=10;
$j /= 5;
echo $j; // 输出2

$k=15;
$k %= 4;
echo $k; // 输出3
?>
```

以下实例演示了使用不同字符串运算符得到的相同结果：


## 实例

```text
<?php
$a = "Hello";
$b = $a . " world!";
echo $b; // 输出Hello world!

$x="Hello";
$x .= " world!";
echo $x; // 输出Hello world!
?>
```


## PHP 递增/递减运算符

以下实例演示了使用递增/递减运算符得到的结果：


## 实例

```text
<?php
$x=10;
echo ++$x; // 输出11

$y=10;
echo $y++; // 输出10

$z=5;
echo --$z; // 输出4

$i=5;
echo $i--; // 输出5
?>
```


## PHP 比较运算符

比较操作符可以让您比较两个值：

以下实例演示了使用一些比较运算符得到的不同结果：


## 实例

```html
<?php
$x=100;
$y="100";

var_dump($x == $y);
echo "<br>";
var_dump($x === $y);
echo "<br>";
var_dump($x != $y);
echo "<br>";
var_dump($x !== $y);
echo "<br>";

$a=50;
$b=90;

var_dump($a > $b);
echo "<br>";
var_dump($a < $b);
?>
```


## PHP 逻辑运算符


## PHP 数组运算符

以下实例演示了使用一些数组运算符得到的不同结果：


## 实例

```text
<?php
$x = array("a" => "red", "b" => "green");
$y = array("c" => "blue", "d" => "yellow");
$z = $x + $y; // $x 和 $y 数组合并
var_dump($z);
var_dump($x == $y);
var_dump($x === $y);
var_dump($x != $y);
var_dump($x <> $y);
var_dump($x !== $y);
?>
```


## 三元运算符

另一个条件运算符是"?:"（或三元）运算符 。


### 语法格式

```text
(expr1) ? (expr2) : (expr3)
```

对 expr1 求值为 TRUE 时的值为 expr2，在 expr1 求值为 FALSE 时的值为 expr3。

自 PHP 5.3 起，可以省略三元运算符中间那部分。表达式 expr1 ?: expr3 在 expr1 求值为 TRUE 时返回 expr1，否则返回 expr3。


### 实例

以下实例中通过判断 $_GET 请求中含有 user 值，如果有返回 $_GET['user']，否则返回 nobody：


## 实例

```text
<?php
// 普通写法
$username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
echo $username, PHP_EOL;

// PHP 5.3+ 版本写法
$username = $_GET['user'] ?: 'nobody';
echo $username, PHP_EOL;
?>
```

注意：PHP_EOL 是一个换行符，兼容更大平台。

在 PHP7+ 版本多了一个 NULL 合并运算符 ??，实例如下：


## 实例

```text
<?php
// 如果 $_GET['user'] 不存在返回 'nobody'，否则返回 $_GET['user'] 的值
$username = $_GET['user'] ?? 'nobody';
// 类似的三元运算符
$username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
?>
```


## 组合比较符(PHP7+)

PHP7+ 支持组合比较符（combined comparison operator）也称之为太空船操作符，符号为 <=>。组合比较运算符可以轻松实现两个变量的比较，当然不仅限于数值类数据的比较。

语法格式如下：

```text
$c = $a <=> $b;
```

解析如下：

- 如果 $a > $b, 则 $c 的值为 1。
- 如果 $a == $b, 则 $c 的值为 0。
- 如果 $a < $b, 则 $c 的值为 -1。

实例如下：


## 实例

```text
<?php
// 整型
echo 1 <=> 1; // 0
echo 1 <=> 2; // -1
echo 2 <=> 1; // 1

// 浮点型
echo 1.5 <=> 1.5; // 0
echo 1.5 <=> 2.5; // -1
echo 2.5 <=> 1.5; // 1

// 字符串
echo "a" <=> "a"; // 0
echo "a" <=> "b"; // -1
echo "b" <=> "a"; // 1
?>
```


## 运算符优先级

下表按照优先级从高到低列出了运算符。同一行中的运算符具有相同优先级，此时它们的结合方向决定求值顺序。

说明：左 ＝ 从左到右，右 ＝ 从右到左。

运算符优先级中，or 和 ||，&& 和 and 都是逻辑运算符，效果一样，但是其优先级却不一样。


## 实例

```java
<?php
// 优先级： &&  >  =  >  and
// 优先级： ||  >  =  >  or

$a = 3;
$b = false;
$c = $a or $b;
var_dump($c);          // 这里的 $c 为 int 值3，而不是 boolean 值 true
$d = $a || $b;
var_dump($d);          //这里的 $d 就是 boolean 值 true
?>
```

以上实例输出结果为：

```text
int(3)
bool(true)
```


### 括号的使用

我们通过括号的配对来明确标明运算顺序，而非靠运算符优先级和结合性来决定，通常能够增加代码的可读性。


## 实例

```text
<?php
// 括号优先运算

$a = 1;
$b = 2;
$c = 3;
$d = $a + $b * $c;
echo $d;
echo "\n";
$e = ($a + $b) * $c;  // 使用括号
echo $e;
echo "\n";
?>
```

以上实例输出结果为：

```text
7
9
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
