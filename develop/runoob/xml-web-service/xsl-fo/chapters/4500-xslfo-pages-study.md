# XSL-FO：XSL-FO 页面

- 来源：[XSLFO 页面](https://www.runoob.com/xslfo/xslfo-pages.html)
- 分类：XML / Web Service
- 技术：XSL-FO
- 笔记类型：学习笔记
- 章节序号：4500

## 本章内容

XSL-FO 使用名为 "Page Masters" 的页面模板来定义页面的布局。


## XSL-FO 页面模板（Page Templates）

XSL-FO 使用名为 "Page Masters" 的页面模板来定义页面的布局。每个模板必须拥有一个唯一的名称：

在上面的实例中，三个 <fo:simple-page-master> 元素，定义了三个不同的模板。每个模板（page-master）都有不同的名称。

第一个模板名为 "intro"。它可作为介绍页面的模板使用。

第二个和第三个模板名为 "left" 和 "right"。它们可作为偶数和奇数页码的页面模板使用。


## XSL-FO 页面尺寸（Page Size）

XSL-FO 使用下面的属性定义页面的尺寸：

- page-width 定义页面的宽度
- page-height 定义页面的高度


## XSL-FO 页面边距（Page Margins）

XSL-FO 使用下面的属性定义页面的边距：

- margin-top 定义上边距
- margin-bottom 定义下边距
- margin-left 定义左边距
- margin-right 定义右边距
- margin 定义所有边的边距


## XSL-FO 页面区（Page Regions）

XSL-FO 使用下面的元素定义页面的区：

- region-body 定义主体区
- region-before 定义顶部区（页眉）
- region-after 定义底部区（页脚）
- region-start 定义左侧区（左侧栏）
- region-end 定义右侧区（右侧栏）

请注意，region-before、region-after、region-start 以及 region-end 是主体区的一部分。为了避免主体区的文本覆盖到这些区域的文本，主体区的边距至少要等于其他区的尺寸。


## XSL-FO 实例

这是从某个 XSL-FO 文档中提取的一个片断：

上面的代码定义了一个名称为 "A4" 的 "Simple Page Master Template"。

页面的宽度是 297 毫米，高度是 210 毫米。

页面的四个边距（上边距、下边距、左边距、右边距）均为 1 厘米。

主体的边距是 3 厘米（四个边都是）。

主体的 before、after、start 以及 end 区均为 2 厘米。

上面的实例中的主体的宽度可通过页面宽度减去左右边距以及 region-body 的边距来计算得出：

297mm - (2 x 1cm) - (2 x 3cm) = 297mm - 20mm - 60mm = 217mm

请注意，region（region-start 和 region-end）没有被计算进来。正如之前讲解过的，这些区（region）是主体的组成部分。


## 复习重点

- 能说明 `XSLFO 页面` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
