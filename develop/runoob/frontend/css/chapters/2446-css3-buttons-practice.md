# CSS：CSS 按钮

- 来源：[CSS3 按钮](https://www.runoob.com/css3/css3-buttons.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2446

## 本章内容

本章节我们为大家介绍使用 CSS 来制作按钮。


## 基本按钮样式

默认按钮 CSS 按钮


## 实例


## 按钮颜色

我们可以使用 background-color 属性来设置按钮颜色:


## 实例

```text
.button1 {background-color: #4CAF50;} /* 绿色 */
.button2 {background-color: #008CBA;} /* 蓝色 */
.button3 {background-color: #f44336;} /* 红色 */
.button4 {background-color: #e7e7e7; color: black;} /* 灰色 */
.button5 {background-color: #555555;} /* 黑色 */
```


## 按钮大小

我们可以使用 font-size 属性来设置按钮大小:


## 实例

```text
.button1 {font-size: 10px;}
.button2 {font-size: 12px;}
.button3 {font-size: 16px;}
.button4 {font-size: 20px;}
.button5 {font-size: 24px;}
```


## 圆角按钮

我们可以使用 border-radius 属性来设置圆角按钮:


## 实例

```text
.button1 {border-radius: 2px;}
.button2 {border-radius: 4px;}
.button3 {border-radius: 8px;}
.button4 {border-radius: 12px;}
.button5 {border-radius: 50%;}
```


## 按钮边框颜色

我们可以使用 border 属性设置按钮边框颜色:


## 实例

```text
.button1 {
    background-color: white;
    color: black;
    border: 2px solid #4CAF50; /* Green */
}
...
```


## 鼠标悬停按钮

我们可以使用 :hover 选择器来修改鼠标悬停在按钮上的样式。

提示: 我们可以使用 transition-duration 属性来设置 "hover" 效果的速度:


## 实例

```text
.button {
    -webkit-transition-duration: 0.4s; /* Safari */
    transition-duration: 0.4s;
}

.button:hover {
    background-color: #4CAF50; /* Green */
    color: white;
}
...
```


## 按钮阴影

我们可以使用 box-shadow 属性来为按钮添加阴影:


## 实例

```text
.button1 {
    box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
}

.button2:hover {
    box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
}
```


## 禁用按钮

我们可以使用 opacity 属性为按钮添加透明度 (看起来类似 "disabled" 属性效果)。

提示: 我们可以添加 cursor 属性并设置为 "not-allowed" 来设置一个禁用的图片:


## 实例

```text
.disabled {
    opacity: 0.6;
    cursor: not-allowed;
}
```


## 按钮宽度

默认情况下，按钮的大小由按钮上的文本内容决定( 根据文本内容匹配长度 )。 我们可以使用 width 属性来设置按钮的宽度:

提示: 如果要设置固定宽度可以使用像素 (px) 为单位，如果要设置响应式的按钮可以设置为百分比。


## 实例

```text
.button1 {width: 250px;}
.button2 {width: 50%;}
.button3 {width: 100%;}
```


## 按钮组

移除外边距并添加 float:left 来设置按钮组:


## 实例

```text
.button {
    float: left;
}
```


## 带边框按钮组

我们可以使用 border 属性来设置带边框的按钮组:


## 实例

```text
.button {
    float: left;
    border: 1px solid green
}
```


## 实例

```text
.btn-group button {
    background-color: #04AA6D; /* 绿色背景 */
    border: 1px solid green; /* 绿色边框 */
    color: white; /* 白色文本 */
    padding: 10px 24px; /* 内边距离、 */
    cursor: pointer; /* 指针/手形图标 */
    float: left; /* 并排浮动按钮 */
}
```


## 按钮动画


## 后续章节

- 实例
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS3 按钮` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
