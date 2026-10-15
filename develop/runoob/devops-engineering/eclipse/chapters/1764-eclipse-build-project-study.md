# Eclipse：Eclipse 编译项目

- 来源：[Eclipse 编译项目](https://www.runoob.com/eclipse/eclipse-build-project.html)
- 分类：DevOps / 工程化
- 技术：Eclipse
- 笔记类型：学习笔记
- 章节序号：1764

## 本章内容

## 编译 Java 项目

一个项目可以关联多个编译器。

java 项目关联的是 java 编译器。可以通过以下方式来查看项目关联的编译器：

- 在 Package Explorer 视图中鼠标右击项目并选择 Properties
- 在左侧的树形菜单中点击 Builders

java编译器用于编译java项目。通过点 New 按钮我们可以让java项目关联 Ant builder 编译器。

java 编译器通过编译 java 项目生成 class 文件。当项目源码发生变化时会自动重新编译 java 代码。

可以通过去除 Project 菜单中 Build Automatically (自动编译)项来禁用自动编译功能。

如果你禁用了自动编译功能，项目需要通过 Project 菜单中的 Build Project 菜单项来编译java项目。 如果勾选了 Build Automatically(自动编译) 项，则 Build Project(手动编译) 菜单项是不可用的。


## 复习重点

- 能说明 `Eclipse 编译项目` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
