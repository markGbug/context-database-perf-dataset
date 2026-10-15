# Markdown：Markdown 高级技巧

- 来源：[Markdown 高级技巧](https://www.runoob.com/markdown/md-advance.html)
- 分类：DevOps / 工程化
- 技术：Markdown
- 笔记类型：练习笔记
- 章节序号：1820

## 本章内容

### 支持的 HTML 元素

不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。

目前支持的 HTML 元素有：<kbd> <b> <i> <em> <sup> <sub> <br>等 ，如：

```html
使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑
```

输出结果为：


### 转义

Markdown 使用了很多特殊符号来表示特定的意义，如果需要显示特定的符号则需要使用转义字符，Markdown 使用反斜杠转义特殊字符：

```text
**文本加粗**
\*\* 正常显示星号 \*\*
```

输出结果为：

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：

```text
\   反斜线
`   反引号
*   星号
_   下划线
{}  花括号
[]  方括号
()  小括号
#   井字号
+   加号
-   减号
.   英文句点
!   感叹号
```


### 公式

Markdown Preview Enhanced 使用 KaTeX 或者 MathJax 来渲染数学表达式。

KaTeX 拥有比 MathJax 更快的性能，但是它却少了很多 MathJax 拥有的特性。你可以查看 KaTeX supported functions/symbols 来了解 KaTeX 支持那些符号和函数。

默认下的分隔符：

- $...$ 或者 \(...\) 中的数学表达式将会在行内显示。
- $$...$$ 或者 \[...\] 或者 ```math 中的数学表达式将会在块内显示。

```text
$$
\begin{Bmatrix}
   a & b \\
   c & d
\end{Bmatrix}
$$
$$
\begin{CD}
   A @>a>> B \\
@VbVV @AAcA \\
   C @= D
\end{CD}
$$
```

输出结果为：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Markdown 高级技巧` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
