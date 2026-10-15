# AppML：<AppML> 案例研究 - 应用程序模型

- 来源：[AppML 案例模型](https://www.runoob.com/appml/appml-case-models.html)
- 分类：后端开发
- 技术：AppML
- 笔记类型：学习笔记
- 章节序号：0707

## 本章内容

此案例研究演示了如何构建一个完整的 <AppML> 互联网应用程序，具有针对数据库中的若干表进行信息列举、编辑和搜索的功能。


## 应用程序模型

在本章中，我们将为数据库中的 Customers 表建立一个完整的应用程序模型。


## <AppML> 过滤器

如需允许过滤 <AppML> 数据，只需简单地向模型添加一个 <filters> 元素：


## 实例：

如需全面了解，请参阅 <AppML> 参考手册。


## <AppML> 更新

如需允许更新 <AppML> 数据，只需简单地向模型添加一个 <update> 元素：


## 实例：

且向 <database> 元素添加一个 <maintable> 和 <keyfield> 元素：


## 实例：

如需全面了解，请参阅 <AppML> 参考手册。


## <AppML> 安全

您可以通过向 <AppML> 标签添加一个 security 属性来很容易地为 <AppML> 模型添加安全。


## 实例：

在上面的实例中，只有用户登录成为用户组 "admin" 的会员才能访问模型。

如需为 <update> 元素设置安全，只需简单地向 <update> 元素添加一个 security 属性：


## 实例：


## 完整的 Customers 模型

在本章中，我们将为数据库中的每个表设立一个应用程序模型。

创建一个名为 Models 的新文件夹。在 Models 文件夹中，为每个应用程序创建一个模型。


## 模型：Customers.xml


## 模型视图

创建一个模型视图，把它保存为 Demo_Model.html，并尝试一下：


## 视图：Demo_Model.htm


## 现在把所有的合并在一起

然后，通过少量 JavaScript 编码，为所有模型创建一个测试页面：


## Demo_Model_Views.htm


## 复习重点

- 能说明 `AppML 案例模型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
