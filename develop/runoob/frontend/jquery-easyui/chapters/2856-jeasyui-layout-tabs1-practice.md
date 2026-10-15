# jQuery EasyUI：jQuery EasyUI 布局 - 创建标签页（Tabs）

- 来源：[jEasyUI 创建标签页](https://www.runoob.com/jeasyui/jeasyui-layout-tabs1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2856

## 本章内容

本教程将向您演示如何使用 easyui 创建一个 Tabs 组件。 Tabs 有多个可以动态地添加或移除的面板（panel）。 您可以使用 Tabs 来在相同的页面上显示不同的实体。

Tabs 一次仅仅显示一个面板（panel），每个面板（panel）都有标题、图标和关闭按钮。 当 Tabs 被选中时，将显示对应的面板（panel）的内容。

从 HTML 标记创建 Tabs，包含一个 DIV 容器和一些 DIV 面板（panel）。

```html
    <div class="easyui-tabs" style="width:400px;height:100px;">
        <div title="First Tab" style="padding:10px;">
            First Tab
        </div>
        <div title="Second Tab" closable="true" style="padding:10px;">
            Second Tab
        </div>
        <div title="Third Tab" iconCls="icon-reload" closable="true" style="padding:10px;">
            Third Tab
        </div>
    </div>
```

我们创建一个带有三个面板（panel）的 Tabs 组件，第二个和第三个面板（panel）可以通过点击关闭按钮进行关闭。


## 下载 jQuery EasyUI 实例

jeasyui-layout-tabs1.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建标签页` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
