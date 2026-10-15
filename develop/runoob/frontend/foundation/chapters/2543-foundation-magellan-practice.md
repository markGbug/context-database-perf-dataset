# Foundation：Foundation 麦哲伦（Magellan）导航

- 来源：[Foundation Magellan](https://www.runoob.com/foundation/foundation-magellan.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2543

## 本章内容

## 如何创建麦哲伦导航

麦哲伦导航就是一个导航索引，创建方式如下:


### 实例


### 实例解析

在 <div> 元素上添加 data-magellan-expedition="fixed" 属性来创建麦哲伦导航。

然后在 <dd> 或 <li> 上添加 data-magellan-arrival="value" 属性，后面添加一个与该属性值一样的链接(page1)。

使用 data-magellan-destination="value" 属性来控制麦哲伦导航的目标, 后面紧跟的 <a> 元素添加 name="value" 属性。两个属性的值必须与 data-magellan-arrival 的值一致 (page1)。

最后，初始化 Foundation JS ，用户在滚动页面时导航就会根据当前显示的内容自动切换。


## 麦哲伦导航头部工具条

麦哲伦导航使用头部工具条实例：


### 实例


## 麦哲伦导航内边距

默认情况下，麦哲伦导航的 <div> 元素有 10px 的内边距。可以使用 CSS 移除它：


### 实例


## 麦哲伦导航选项

使用 data-options 属性修改麦哲伦导航的设置, 例如 <div data-magellan-expedition="fixed" data-options="destination_threshold:60">:


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation Magellan` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
