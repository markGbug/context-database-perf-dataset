# Bootstrap4：Bootstrap4 文字排版

- 来源：[Bootstrap4 文字排版](https://www.runoob.com/bootstrap4/bootstrap4-typography.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2307

## 本章内容

## Bootstrap 4 默认设置

Bootstrap 4 默认的 font-size 为 16px, line-height 为 1.5。

默认的 font-family 为 "Helvetica Neue", Helvetica, Arial, sans-serif。

此外，所有的 <p> 元素 margin-top: 0 、 margin-bottom: 1rem (16px)。


## <h1> - <h6>

Bootstrap 中定义了所有的 HTML 标题（h1 到 h6）的样式。请看下面的实例：


## 实例

```html
<div class="container">
  <h1>h1 Bootstrap 标题 (2.5rem = 40px)</h1>
  <h2>h2 Bootstrap 标题 (2rem = 32px)</h2>
  <h3>h3 Bootstrap 标题 (1.75rem = 28px)</h3>
  <h4>h4 Bootstrap 标题 (1.5rem = 24px)</h4>
  <h5>h5 Bootstrap 标题 (1.25rem = 20px)</h5>
  <h6>h6 Bootstrap 标题 (1rem = 16px)</h6>
</div>
```


### Display 标题类

Bootstrap 还提供了四个 Display 类来控制标题的样式: .display-1, .display-2, .display-3, .display-4。


## 实例

```html
<div class="container">
  <h1>Display 标题</h1>
  <p>Display 标题可以输出更大更粗的字体样式。</p>
  <h1 class="display-1">Display 1</h1>
  <h1 class="display-2">Display 2</h1>
  <h1 class="display-3">Display 3</h1>
  <h1 class="display-4">Display 4</h1>
</div>
```


## <small>

在 Bootstrap 4 中 HTML <small> 元素用于创建字号更小的颜色更浅的文本:


## 实例

```html
<div class="container">
  <h1>更小文本标题</h1>
  <p>small 元素用于字号更小的颜色更浅的文本:</p>
  <h1>h1 标题 <small>副标题</small></h1>
  <h2>h2 标题 <small>副标题</small></h2>
  <h3>h3 标题 <small>副标题</small></h3>
  <h4>h4 标题 <small>副标题</small></h4>
  <h5>h5 标题 <small>副标题</small></h5>
  <h6>h6 标题 <small>副标题</small></h6>
</div>
```


## <mark>

Bootstrap 4 定义 <mark> 为黄色背景及有一定的内边距:


## 实例

```html
<div class="container">
  <h1>高亮文本</h1>
  <p>使用 mark 元素来 <mark>高亮</mark> 文本。</p>
</div>
```


## <abbr>

Bootstrap 4 定义 HTML <abbr> 元素的样式为显示在文本底部的一条虚线边框:


## 实例

```html
<div class="container">
  <h1>Abbreviations</h1>
  <p>The abbr element is used to mark up an abbreviation or acronym:</p>
  <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>
</div>
```


## <blockquote>

对于引用的内容可以在 <blockquote> 上添加 .blockquote 类 :


## 实例

```html
<div class="container">
  <h1>Blockquotes</h1>
  <p>The blockquote element is used to present content from another source:</p>
  <blockquote class="blockquote">
    <p>For 50 years, WWF has been protecting the future of nature. The world's leading conservation organization, WWF works in 100 countries and is supported by 1.2 million members in the United States and close to 5 million globally.</p>
    <footer class="blockquote-footer">From WWF's website</footer>
  </blockquote>
</div>
```


## <dl>

Bootstrap 4 定义 HTML <dl> 元素的样式如下:


## 实例

```html
<div class="container">
  <h1>Description Lists</h1>
  <p>The dl element indicates a description list:</p>
  <dl>
    <dt>Coffee</dt>
    <dd>- black hot drink</dd>
    <dt>Milk</dt>
    <dd>- white cold drink</dd>
  </dl>
</div>
```


## <code>

Bootstrap 4 定义 HTML <code> 元素的样式如下:


## 实例

```html
<div class="container">
  <h1>代码片段</h1>
  <p>可以将一些代码元素放到 code 元素里面:</p>
  <p>以下 HTML 元素: <code>span</code>, <code>section</code>, 和 <code>div</code> 用于定义部分文档内容。</p>
</div>
```


## <kbd>

Bootstrap 4 定义 HTML <kbd> 元素的样式如下:


## 实例

```java
<div class="container">
  <h1>Keyboard Inputs</h1>
  <p>To indicate input that is typically entered via the keyboard, use the kbd element:</p>
  <p>Use <kbd>ctrl + p</kbd> to open the Print dialog box.</p>
</div>
```


## <pre>

Bootstrap 4 定义 HTML <pre> 元素的样式如下:


## 实例

```html
<div class="container">
<h1>Multiple Code Lines</h1>
<p>For multiple lines of code, use the pre element:</p>
<pre>
Text in a pre element
is displayed in a fixed-width
font, and it preserves
both      spaces and
line breaks.
</pre>
</div>
```


## 更多排版类

下表提供了 Bootstrap4 更多排版类的实例：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 文字排版` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
