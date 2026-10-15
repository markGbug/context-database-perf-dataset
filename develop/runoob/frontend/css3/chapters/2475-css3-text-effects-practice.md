# CSS3：CSS3 文本效果

- 来源：[CSS3 文本效果](https://www.runoob.com/css3/css3-text-effects.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：练习笔记
- 章节序号：2475

## 本章内容

## CSS3 文本效果

CSS3中包含几个新的文本特征。

在本章中您将了解以下文本属性：

- text-shadow
- box-shadow
- text-overflow
- word-wrap
- word-break


## 浏览器支持


## CSS3 的文本阴影

CSS3 中，text-shadow属性适用于文本阴影。

您指定了水平阴影，垂直阴影，模糊的距离，以及阴影的颜色：


## 实例

给标题添加阴影:

```text
h1
{
    text-shadow: 5px 5px 5px #FF0000;
}
```


## CSS3 box-shadow属性

CSS3 中 CSS3 box-shadow 属性适用于盒子阴影


## 实例

```text
div {
    box-shadow: 10px 10px 5px #888888;
}
```


## 接下来给阴影添加颜色


## 实例

```text
div {
    box-shadow: 10px 10px grey;
}
```


## 接下来给阴影添加一个模糊效果


## 实例

```text
div {
    box-shadow: 10px 10px 5px grey;
}
```


## 你也可以在 ::before 和 ::after 两个伪元素中添加阴影效果


## 实例

```text
#boxshadow {
    position: relative;
    box-shadow: 1px 2px 4px rgba(0, 0, 0, .5);
    padding: 10px;
    background: white;
}
#boxshadow img {
     width: 100%;
     border: 1px solid #8a4419;
     border-style: inset;
}
#boxshadow::after {
    content: '';
    position: absolute;
    z-index: -1; /* hide shadow behind image */
    box-shadow: 0 15px 20px rgba(0, 0, 0, 0.3);
    width: 70%;
    left: 15%; /* one half of the remaining 30% */
    height: 100px;
    bottom: 0;
}
```


## 阴影的一个使用特例是卡片效果


## 实例

```text
div.card {
    width: 250px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    text-align: center;
}
```


## CSS3 Text Overflow属性

CSS3文本溢出属性指定应向用户如何显示溢出内容


## 实例

```text
p.test1 {
    white-space: nowrap;
    width: 200px;
    border: 1px solid #000000;
    overflow: hidden;
    text-overflow: clip;
}

p.test2 {
    white-space: nowrap;
    width: 200px;
    border: 1px solid #000000;
    overflow: hidden;
    text-overflow: ellipsis;
}
```


## CSS3的换行

如果某个单词太长，不适合在一个区域内，它扩展到外面：

CSS3中，自动换行属性允许您强制文本换行 - 即使这意味着分裂它中间的一个字：

CSS代码如下：


## 实例

允许长文本换行:

```text
p {word-wrap:break-word;}
```


## CSS3 单词拆分换行

CSS3 单词拆分换行属性指定换行规则：

CSS代码如下：


## 实例

```text
p.test1 {
    word-break: keep-all;
}

p.test2 {
    word-break: break-all;
}
```


## 新文本属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS3 文本效果` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
