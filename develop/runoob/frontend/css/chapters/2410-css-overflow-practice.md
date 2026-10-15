# CSS：CSS 布局 - Overflow

- 来源：[CSS Overflow](https://www.runoob.com/css/css-overflow.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2410

## 本章内容

CSS overflow 属性用于控制内容溢出元素框时显示的方式。

这里的文本内容是可以滚动的，滚动条方向是垂直方向。

尝试一下 »


## CSS Overflow

CSS overflow 属性可以控制内容溢出元素框时在对应的元素区间内添加滚动条。

overflow属性有以下值：

注意:overflow 属性只工作于指定高度的块元素上。

注意: 在 OS X Lion ( Mac 系统) 系统上，滚动条默认是隐藏的，使用的时候才会显示 (设置 "overflow:scroll" 也是一样的)。


## overflow: visible

默认情况下，overflow 的值为 visible， 意思是内容溢出元素框：

这里的文本内容会溢出元素框。


## 实例

```text
div {
    width: 200px;
    height: 50px;
    background-color: #eee;
    overflow: visible;
}
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS Overflow` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
