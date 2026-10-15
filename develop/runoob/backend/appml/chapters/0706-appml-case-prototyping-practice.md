# AppML：<AppML> 案例研究 - 原型

- 来源：[AppML 案例原型](https://www.runoob.com/appml/appml-case-prototyping.html)
- 分类：后端开发
- 技术：AppML
- 笔记类型：练习笔记
- 章节序号：0706

## 本章内容

此案例研究演示了如何构建一个完整的 <AppML> 互联网应用程序，具有针对数据库中的若干表进行信息列举、编辑和搜索的功能。


## 原型

在本章中，我们将为数据库中的每个表建立一个原型模型。

原型是非常便于使用的开发应用程序的起点。


## 原型模型

首先，为原型创建一个文件夹。该文件夹命名为 Prototypes。

然后，为数据库中的每个表创建一个原型模型。

使用 SELECT * from 每个表，并保存模型为 XML 文件：


## 模型：Proto_Customers.xml


## 模型：Proto_Suppliers.xml


## 模型：Proto_Products.xml


## 原型视图

创建一个原型视图，把它保存为 Demo_Prototype.html，并尝试一下：


## 视图：Demo_Prototype.htm


## 现在把所有的合并在一起

最后，通过少量 JavaScript 编码，为所有原型模型创建一个简单的原型页面：


## Demo_Prototype_Views.htm


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AppML 案例原型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
