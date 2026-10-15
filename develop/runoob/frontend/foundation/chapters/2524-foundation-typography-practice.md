# Foundation：Foundation 文本

- 来源：[Foundation 文本](https://www.runoob.com/foundation/foundation-typography.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2524

## 本章内容

## Foundation 默认设置

Foundation 使用浏览器默认字体大小 (font-size:100%)。对于大多数桌面浏览器来说，字体默认为 16px。对于大多数移动端浏览器来说，字体默认为 12px。默认的字体为 "Helvetica Neue"， line-height 默认为 1.5。

以上默认的设置均是针对 <body> 元素。


## Foundation 文字排列设计

本章节我们将讨论 Foundation 的文字排列设计。

以下实例的真实样式请通过点击"尝试一下"按钮查看。


## <h1> - <h6>

Foundation 渲染的 HTML 标题 (<h1> 到 <h6>) 如下所示:


### 实例

```html
<h1>h1 标题</h1>
<h2>h2 标题</h2>
<h3>h3 标题</h3>
<h4>h4 标题</h4>
<h5>h5 标题</h5>
<h6>h6 标题</h6>
```

提示： 如果需要创建一个浅色的标题，可以在元素上添加 .subheader 类:


### 实例

```html
<h1 class="subheader">h1.subheader</h1>
<h2 class="subheader">h2.subheader</h2>
<h3 class="subheader">h3.subheader</h3>
<h4 class="subheader">h4.subheader</h4>
<h5 class="subheader">h5.subheader</h5>
<h6 class="subheader">h6.subheader</h6>
```


## <small>

在 Foundation 中， HTML <small> 元素用于创建一个浅色的副标题：


### 实例

```html
<h1>h1 heading <small>secondary text</small></h1>
<h2>h2 heading <small>secondary text</small></h2>
<h3>h3 heading <small>secondary text</small></h3>
<h4>h4 heading <small>secondary text</small></h4>
<h5>h5 heading <small>secondary text</small></h5>
<h6>h6 heading <small>secondary text</small></h6>
```


## <a>

Foundation <a> 元素的样式如下所示：


### 实例

```html
<p>这是一个 <a class="a" href="#">链接</a>。</p>
```


## <abbr>

Foundation <abbr> 元素的样式如下所示：


### 实例

```html
<p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
```


## <blockquote>

Foundation <blockquote> 元素的样式如下所示：


### 实例

```html
<blockquote>
  <p>学的不仅是技术，更是梦想！</p>
  <cite>菜鸟教程</cite>
</blockquote>
```


## <dl>

Foundation <dl> 元素的样式如下所示：


### 实例

```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```


## <code>

Foundation <code> 元素的样式如下所示：


### 实例

```html
<p>以下 HTML 元素: <code>span</code>, <code>section</code>, 和 <code>div</code> 是文档的一部分。</p>
```


## <kbd>

Foundation <kbd> 元素的样式如下所示：


### 实例

```html
<p>按下 <kbd>ctrl + p</kbd> 键打开打印窗口。</p>
```


## <hr>

Foundation <hr> 元素的样式如下所示：


### 实例

```html
<hr>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 文本` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
