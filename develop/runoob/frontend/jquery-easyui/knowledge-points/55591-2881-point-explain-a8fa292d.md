# 知识点 55591：jQuery EasyUI：jEasyUI 扩展行显示细节 - 本章内容

- 来源：[jEasyUI 扩展行显示细节](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid21.html)
- 来源章节：[2881-jeasyui-datagrid-datagrid21-practice.md](../chapters/2881-jeasyui-datagrid-datagrid21-practice.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：解释
- 原章节序号：2881

## 原文片段

我们定义 'detailFormatter' 函数，告诉数据网格（datagrid）如何渲染详细视图。在这种情况下,我们返回一个简单的 '<div>' 元素，它将充当详细内容的容器。请注意，详细信息为空。当用户点击展开按钮（'+'）时，onExpandRow 事件将被触发。所以我们可以写一些代码来加载 ajax 详细内容。最后我们调用 'fixDetailRowHeight' 方法来固定当详细内容加载时的行高度。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 扩展行显示细节` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
