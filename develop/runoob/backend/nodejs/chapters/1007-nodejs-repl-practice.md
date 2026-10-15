# Node.js：Node.js REPL(交互式解释器)

- 来源：[Node.js REPL](https://www.runoob.com/nodejs/nodejs-repl.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1007

## 本章内容

Node.js 提供了一个内置的 REPL（Read-Eval-Print Loop），这是一个交互式编程环境，可以在终端中运行 JavaScript 代码。REPL 的名称来源于它的主要操作：读取（Read）、执行（Eval）、打印（Print）和循环（Loop）。

Node 自带了交互式解释器，可以执行以下任务：

- 读取（Read） - 读取用户输入，解析输入的 Javascript 数据结构并存储在内存中。
- 执行（Eval） - 执行输入的数据结构
- 打印（Print） - 输出结果
- 循环（Loop） - 循环操作以上步骤直到用户两次按下 ctrl-c 按钮退出。

REPL 可以直接输入并立即执行 JavaScript 代码，快速验证代码片段。

REPL 适合测试简单逻辑和调试以及尝试新语法或 Node.js API。

开始学习 REPL

我们可以输入以下命令来启动 Node 的终端：

```text
node
```

执行后出现如下内容：

```text
# node
Welcome to Node.js v20.1.0.
Type ".help" for more information.
>
```

这时我们就可以在 > 后输入简单的表达式，并按下回车键来计算结果。


### 简单的表达式运算

接下来让我们在 Node.js REPL 的命令行窗口中执行简单的数学运算：

```text
$ node
> 1 +4
5
> 5 / 2
2.5
> 3 * 6
18
> 4 - 1
3
> 1 + ( 2 * 3 ) - 4
3
>
```


### 使用变量

你可以将数据存储在变量中，并在你需要的时候使用它。

变量声明需要使用 var 关键字，如果没有使用 var 关键字变量会直接打印出来。

使用 var 关键字的变量可以使用 console.log() 来输出变量。

```javascript
$ node
> x = 10
10
> var y = 10
undefined
> x + y
20
> console.log("Hello World")
Hello World
undefined
> console.log("www.runoob.com")
www.runoob.com
undefined
```


### 多行表达式

Node REPL 支持输入多行表达式，这就有点类似 JavaScript。接下来让我们来执行一个 do-while 循环：

```java
$ node
> var x = 0
undefined
> do {
... x++;
... console.log("x: " + x);
... } while ( x < 5 );
x: 1
x: 2
x: 3
x: 4
x: 5
undefined
>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js REPL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
