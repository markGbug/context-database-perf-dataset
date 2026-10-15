# CSS：CSS id 和 class

- 来源：[CSS Id 和 Class选择器](https://www.runoob.com/css/css-id-class.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2393

## 本章内容

## id 和 class 选择器

如果你要在HTML元素中设置CSS样式，你需要在元素中设置"id" 和 "class"选择器。


## id 选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。

HTML元素以id属性来设置id选择器,CSS 中 id 选择器以 "#" 来定义。

以下的样式规则应用于元素属性 id="para1":


## 实例

```text
#para1
{
    text-align:center;
    color:red;
}
```

ID属性不要以数字开头，数字开头的ID在 Mozilla/Firefox 浏览器中不起作用。


## class 选择器

class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在多个元素中使用。

class 选择器在 HTML 中以 class 属性表示, 在 CSS 中，类选择器以一个点 . 号显示：

在以下的例子中，所有拥有 center 类的 HTML 元素均为居中。


## 实例

```text
.center {text-align:center;}
```

你也可以指定特定的 HTML 元素使用 class。

在以下实例中, 所有的 p 元素使用 class="center" 让该元素的文本居中:


## 实例

```text
p.center {text-align:center;}
```

多个 class 选择器可以使用空格分开：


## 实例

```text
.center { text-align:center; }
.color { color:#ff0000; }
```

类名的第一个字符不能使用数字！它无法在 Mozilla 或 Firefox 中起作用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS Id 和 Class选择器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
