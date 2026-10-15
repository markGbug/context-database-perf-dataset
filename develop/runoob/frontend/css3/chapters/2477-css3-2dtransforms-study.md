# CSS3：CSS3 2D 转换

- 来源：[CSS3 2D 转换](https://www.runoob.com/css3/css3-2dtransforms.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：学习笔记
- 章节序号：2477

## 本章内容

## CSS3 转换

CSS3 转换可以对元素进行移动、缩放、转动、拉长或拉伸。


## 它是如何工作？

转换的效果是让某个元素改变形状，大小和位置。

您可以使用 2D 或 3D 转换来转换您的元素。

鼠标移动到以下元素上，查看 2D 和 3D 的转换效果：


## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

紧跟在 -webkit-, -ms- 或 -moz- 前的数字为支持该前缀属性的第一个浏览器版本号。

Internet Explorer 10, Firefox, 和 Opera支持transform 属性.

Chrome 和 Safari 要求前缀 -webkit- 版本.

注意： Internet Explorer 9 要求前缀 -ms- 版本.


## 2D 转换

在本章您将了解2D变换方法：

- translate()
- rotate()
- scale()
- skew()
- matrix()

在下一章中您将了解3D转换。


## 实例

```text
div
{
transform: rotate(30deg);
-ms-transform: rotate(30deg); /* IE 9 */
-webkit-transform: rotate(30deg); /* Safari and Chrome */
}
```


## translate() 方法

translate()方法，根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。


## 实例

```text
div
{
transform: translate(50px,100px);
-ms-transform: translate(50px,100px); /* IE 9 */
-webkit-transform: translate(50px,100px); /* Safari and Chrome */
}
```

translate值（50px，100px）是从左边元素移动50个像素，并从顶部移动100像素。


## rotate() 方法

rotate()方法，在一个给定度数顺时针旋转的元素。负值是允许的，这样是元素逆时针旋转。


## 实例

```text
div
{
transform: rotate(30deg);
-ms-transform: rotate(30deg); /* IE 9 */
-webkit-transform: rotate(30deg); /* Safari and Chrome */
}
```

rotate值（30deg）元素顺时针旋转30度。


## scale() 方法

scale()方法，该元素增加或减少的大小，取决于宽度（X轴）和高度（Y轴）的参数：


## 实例

```text
-ms-transform:scale(2,3); /* IE 9 */
-webkit-transform: scale(2,3); /* Safari */
transform: scale(2,3); /* 标准语法 */
```

scale（2,3）转变宽度为原来的大小的2倍，和其原始大小3倍的高度。


## skew() 方法


### 语法

```html
transform:skew(<angle> [,<angle>]);
```

包含两个参数值，分别表示X轴和Y轴倾斜的角度，如果第二个参数为空，则默认为0，参数为负表示向相反方向倾斜。

- skewX(<angle>);表示只在X轴(水平方向)倾斜。
- skewY(<angle>);表示只在Y轴(垂直方向)倾斜。


## 实例

```text
div
{
transform: skew(30deg,20deg);
-ms-transform: skew(30deg,20deg); /* IE 9 */
-webkit-transform: skew(30deg,20deg); /* Safari and Chrome */
}
```

skew(30deg,20deg) 元素在 X 轴和 Y 轴上倾斜 20 度 30 度。


## matrix() 方法

matrix()方法和2D变换方法合并成一个。

matrix 方法有六个参数，包含旋转，缩放，移动（平移）和倾斜功能。


## 实例

利用matrix()方法旋转div元素30°

```text
div
{
transform:matrix(0.866,0.5,-0.5,0.866,0,0);
-ms-transform:matrix(0.866,0.5,-0.5,0.866,0,0); /* IE 9 */
-webkit-transform:matrix(0.866,0.5,-0.5,0.866,0,0); /* Safari and Chrome */
}
```


## 新转换属性

以下列出了所有的转换属性:


## 2D 转换方法


## 复习重点

- 能说明 `CSS3 2D 转换` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
