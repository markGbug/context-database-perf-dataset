# jQuery EasyUI：jQuery EasyUI 插件

- 来源：[jQuery EasyUI 插件](https://www.runoob.com/jeasyui/jeasyui-ref-plugins.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2906

## 本章内容

jQuery EasyUI 提供了用于创建跨浏览器网页的完整的组件集合，包括功能强大的 datagrid（数据网格）、treegrid（树形表格）、 panel（面板）、combo（下拉组合）等等。 用户可以组合使用这些组件，也可以单独使用其中一个。


## 插件列表


### Base（基础）

- Parser 解析器
- Easyloader 加载器
- Draggable 可拖动
- Droppable 可放置
- Resizable 可调整尺寸
- Pagination 分页
- Searchbox 搜索框
- Progressbar 进度条
- Tooltip 提示框


### Layout（布局）

- Panel 面板
- Tabs 标签页/选项卡
- Accordion 折叠面板
- Layout 布局


### Menu（菜单）与 Button（按钮）

- Menu 菜单
- Linkbutton 链接按钮
- Menubutton 菜单按钮
- Splitbutton 分割按钮


### Form（表单）

- Form 表单
- Validatebox 验证框
- Combo 组合
- Combobox 组合框
- Combotree 组合树
- Combogrid 组合网格
- Numberbox 数字框
- Datebox 日期框
- Datetimebox 日期时间框
- Calendar 日历
- Spinner 微调器
- Numberspinner 数值微调器
- Timespinner 时间微调器
- Slider 滑块


### Window（窗口）

- Window 窗口
- Dialog 对话框
- Messager 消息框


### DataGrid（数据网格）与 Tree（树）

- Datagrid 数据网格
- Propertygrid 属性网格
- Tree 树
- Treegrid 树形网格


## 插件

easyui 的每个组件都有属性、方法和事件。用户可以很容易地对这些组件进行扩展。


### 属性

属性是定义在 jQuery.fn.{plugin}.defaults。比如，dialog 的属性是定义在 jQuery.fn.dialog.defaults。


### 事件

事件（回调函数）也是定义在 jQuery.fn.{plugin}.defaults。


### 方法

调用方法的语法：$('selector').plugin('method', parameter);

其中：

- selector 是 jquery 对象选择器。
- plugin 是插件名称。
- method 是与插件相匹配的已存在方法。
- parameter 是参数对象，可以是对象、字符串...

方法是定义在 jQuery.fn.{plugin}.methods。每个方法有两个参数：jq 和 param。第一个参数 'jq' 是必需的，引用 jQuery 对象。第二个参数 'param' 引用方法传递的实际参数。比如，要扩展 dialog 组件的方法名为 'mymove' 的方法，代码如下：

```text
$.extend($.fn.dialog.methods, {
    mymove: function(jq, newposition){
        return jq.each(function(){
            $(this).dialog('move', newposition);
        });
    }
});
```

现在您可以调用 'mymove' 方法来移动对话框（dialog）到指定的位置：

```text
$('#dd').dialog('mymove', {
    left: 200,
    top: 100
});
```


## 开始使用 jQuery EasyUI

下载库，并在您的页面中引用 EasyUI CSS 和 JavaScript 文件。

```html
<link rel="stylesheet" type="text/css" href="easyui/themes/default/easyui.css">
<link rel="stylesheet" type="text/css" href="easyui/themes/icon.css">
<script type="text/javascript" src="easyui/jquery-1.7.2.min.js"></script>
<script type="text/javascript" src="easyui/jquery.easyui.min.js"></script>
```

一旦您引用了 EasyUI 必要的文件，您就可以通过标记或者使用 JavaScript 来定义一个 EasyUI 组件。比如，要顶一个带有可折叠功能的面板，您需要编写如下 HTML 代码：

```html
<div id="p" class="easyui-panel" style="width:500px;height:200px;padding:10px;"
    title="My Panel" iconCls="icon-save" collapsible="true">
    The panel content
</div>
```

当通过标记创建组件，'data-options' 属性被用来支持自版本 1.3 以来 HTML5 兼容的属性名称。所以您可以如下重写上面的代码：

```html
<div id="p" class="easyui-panel" style="width:500px;height:200px;padding:10px;"
    title="My Panel" data-options="iconCls:'icon-save',collapsible:true">
    The panel content
</div>
```

下面的代码演示了如何创建一个绑定 'onSelect' 事件的组合框。

```html
<input class="easyui-combobox" name="language"
    data-options="
    url:'combobox_data.json',
    valueField:'id',
    textField:'text',
    panelHeight:'auto',
    onSelect:function(record){
    alert(record.text)
    }">
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery EasyUI 插件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
