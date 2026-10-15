# CSS：CSS 网页布局

- 来源：[CSS 网页布局](https://www.runoob.com/css/css-website-layout.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2426

## 本章内容

## 网页布局

网页布局有很多种方式，一般分为以下几个部分：头部区域、菜单导航区域、内容区域、底部区域。


## 头部区域

头部区域位于整个网页的顶部，一般用于设置网页的标题或者网页的 logo：


## CSS3 实例

```text
.header {
  background-color: #F1F1F1;
  text-align: center;
  padding: 20px;
}
```


## 菜单导航区域

菜单导航条包含了一些链接，可以引导用户浏览其他页面：


## CSS3 实例

```text
/* 导航条 */
.topnav {
  overflow: hidden;
  background-color: #333;
}

/* 导航链接 */
.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* 链接 - 修改颜色 */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}
```


## 内容区域

内容区域一般有三种形式:

- 1 列：一般用于移动端
- 2 列：一般用于平板设备
- 3 列：一般用于 PC 桌面设备

我们将创建一个 3 列布局，在小的屏幕上将会变成 1 列布局（响应式）：


## CSS3 实例

```text
/* 创建三个相等的列 */
.column {
  float: left;
  width: 33.33%;
}

/* 列后清除浮动 */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* 响应式布局 - 小于 600 px 时改为上下布局 */
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
  }
}
```

提示:要设置两列可以设置 width 为 50%。创建 4 列可以设置为 25%。

提示:如果你想了解更多 @media 的规则可以查看 CSS3 多媒体查询。

提示: 现在更高级的方式是使用 CSS Flexbox 来创建列的布局，但 Internet Explorer 10 及更早的版本不支持该方式， IE6-10 可以使用浮动方式。 CSS Flexbox 的更多内容可以查看 CSS3 弹性盒子(Flex Box)。


### 不相等的列

不相等的列一般是在中间部分设置内容区域，这块也是最大最主要的，左右两次侧可以作为一些导航等相关内容，这三列加起来的宽度是 100％。


## CSS3 实例

```text
.column {
  float: left;
}

/* 左右侧栏的宽度 */
.column.side {
  width: 25%;
}

/* 中间列宽度 */
.column.middle {
  width: 50%;
}

/* 响应式布局 - 宽度小于600px时设置上下布局 */
@media screen and (max-width: 600px) {
  .column.side, .column.middle {
    width: 100%;
  }
}
```


## 底部区域

底部区域在网页的最下方，一般包含版权信息和联系方式等。


## CSS3 实例

```text
.footer {
  background-color: #F1F1F1;
  text-align: center;
  padding: 10px;
}
```


## 响应式网页布局

通过以上等学习我们来创建一个响应式等页面，页面的布局会根据屏幕的大小来调整：


## CSS3 实例

```text
* {
  box-sizing: border-box;
}

body {
  font-family: Arial;
  padding: 10px;
  background: #f1f1f1;
}

/* 头部标题 */
.header {
  padding: 30px;
  text-align: center;
  background: white;
}

.header h1 {
  font-size: 50px;
}

/* 导航条 */
.topnav {
  overflow: hidden;
  background-color: #333;
}

/* 导航条链接 */
.topnav a {
  float: left;
  display: block;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

/* 链接颜色修改 */
.topnav a:hover {
  background-color: #ddd;
  color: black;
}

/* 创建两列 */
/* Left column */
.leftcolumn {
  float: left;
  width: 75%;
}

/* 右侧栏 */
.rightcolumn {
  float: left;
  width: 25%;
  background-color: #f1f1f1;
  padding-left: 20px;
}

/* 图像部分 */
.fakeimg {
  background-color: #aaa;
  width: 100%;
  padding: 20px;
}

/* 文章卡片效果 */
.card {
  background-color: white;
  padding: 20px;
  margin-top: 20px;
}

/* 列后面清除浮动 */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* 底部 */
.footer {
  padding: 20px;
  text-align: center;
  background: #ddd;
  margin-top: 20px;
}

/* 响应式布局 - 屏幕尺寸小于 800px 时，两列布局改为上下布局 */
@media screen and (max-width: 800px) {
  .leftcolumn, .rightcolumn {
    width: 100%;
    padding: 0;
  }
}

/* 响应式布局 -屏幕尺寸小于 400px 时，导航等布局改为上下布局 */
@media screen and (max-width: 400px) {
  .topnav a {
    float: none;
    width: 100%;
  }
}
```


## 复习重点

- 能说明 `CSS 网页布局` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
