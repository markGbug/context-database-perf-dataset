# VBScript：VBScript 关键字

- 来源：[VB 关键字](https://www.runoob.com/vbscript/vbscript-ref-keywords.html)
- 分类：后端开发
- 技术：VBScript
- 笔记类型：学习笔记
- 章节序号：1216

## 本章内容

## VBScript 关键字

用于指示一个未初始化的变量值。当第一次创建变量时或变量值显式设置为空时，变量值未初始化且变量未被赋值。

实例： Dim x '变量 x 未初始化！ x="ff" '变量 x 不再是未初始化 x=Empty '变量 x 未初始化！

注意：这和 Null 不一样！！

用于测试一个变量是否未初始化。

实例：If (IsEmpty(x)) '变量 x 未初始化？

实例: Set myObject=Nothing

实例：If (myObject Is Nothing) '它是否未设置？

注意：如果您把一个值与 Nothing 作比较，您将不会得到正确的结果！实例: If (myObject = Nothing) '总是错误！

Null 把值设置为"无效"，Empty 则表示值"未设置"。

注意：这不同于 Empty 或 Nothing！！

实例：x=Null 'x 不包含有效数据

实例: if (IsNull(x)) 'x 是无效的？


## 复习重点

- 能说明 `VB 关键字` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
