# Bootstrap4：Bootstrap4 图像形状

- 来源：[Bootstrap4 图像形状](https://www.runoob.com/bootstrap4/bootstrap4-images.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2310

## 本章内容

## 圆角图片

.rounded 类可以让图片显示圆角效果：


## 实例

```html
<img src="cinqueterre.jpg" class="rounded" alt="Cinque Terre">
```


## 椭圆图片

.rounded-circle 类可以设置椭圆形图片:


## 实例

```html
<img src="cinqueterre.jpg" class="rounded-circle" alt="Cinque Terre">
```


## 缩略图

.img-thumbnail 类用于设置图片缩略图(图片有边框):


## 实例

```html
<img src="cinqueterre.jpg" class="img-thumbnail" alt="Cinque Terre">
```


## 图片对齐方式

使用 .float-right 类来设置图片右对齐，使用 .float-left 类设置图片左对齐:


## 实例

```html
<img src="paris.jpg" class="float-left">
<img src="cinqueterre.jpg" class="float-right">
```


## 图片居中

使用 .mx-auto (margin:auto) 和 .d-block (display:block) 类来设置图片居中对齐：


## 实例

```html
<img src="paris.jpg" class="mx-auto d-block">
```


## 响应式图片

图像有各种各样的尺寸，我们需要根据屏幕的大小自动适应。

我们可以通过在 <img> 标签中添加 .img-fluid 类来设置响应式图片。

.img-fluid 类设置了 max-width: 100%; 、 height: auto; :


## 实例

```html
<img class="img-fluid" src="img_chania.jpg" alt="Chania">
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 图像形状` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
