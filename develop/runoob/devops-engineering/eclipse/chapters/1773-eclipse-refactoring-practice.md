# Eclipse：Eclipse 重构菜单

- 来源：[Eclipse 重构菜单](https://www.runoob.com/eclipse/eclipse-refactoring.html)
- 分类：DevOps / 工程化
- 技术：Eclipse
- 笔记类型：练习笔记
- 章节序号：1773

## 本章内容

## 使用Eclipse重构

在项目开发中我们经常需要修改类名，但如果其他类依赖该类时，我们就需要花很多时间去修改类名。

但 Eclipse 重构功能可以自动检测类的依赖关系并修改类名，帮我们节省了很多时间。

可用过以下方式打开重构菜单：

- 在 Package Explorer 视图中右击 Java 元素并选择Refactor(重构)菜单项
- 在 Java 编辑器中鼠标右击 Java 元素并选择Refactor(重构)菜单项
- 在 Package Explorer 视图中选择 Java 元素并按下 Shift + Alt + T

下图中我们在Java 编辑器中选中了 HelloWorld 类：

在选择 Rename 后会提示输入新的类名并按回车结束修改：

在修改完成按下回车键后，会弹出将将会修改的类：

你只需点击 Continue 按钮即可完成操作。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Eclipse 重构菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
