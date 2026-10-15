# 知识点 16430：jQuery EasyUI：jEasyUI 创建 CRUD 数据网格 - 本章内容

- 来源：[jEasyUI 创建 CRUD 数据网格](https://www.runoob.com/jeasyui/jeasyui-app-crud2.html)
- 来源章节：[2843-jeasyui-app-crud2-study.md](../chapters/2843-jeasyui-app-crud2-study.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2843

## 原文片段

```text
<table id="dg" title="My Users" style="width:550px;height:250px"
        toolbar="#toolbar" idField="id"
        rownumbers="true" fitColumns="true" singleSelect="true">
    <thead>
        <tr>
            <th field="firstname" width="50" editor="{type:'validatebox',options:{required:true}}">First Name</th>
            <th field="lastname" width="50" editor="{type:'validatebox',options:{required:true}}">Last Name</th>
            <th field="phone" width="50" editor="text">Phone</th>
            <th field="email" width="50" editor="{type:'validatebox',options:{validType:'email'}}">Email</th>
        </tr>
    </thead>
</table>
<div id="toolbar">
    <a href="#" class="easyui-linkbutton" iconCls="icon-add" plain="true" onclick="javascript:$('#dg').edatagrid('addRow')">New</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-remove" plain="true" onclick="javascript:$('#dg').edatagrid('destroyRow')">Destroy</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-save" plain="true" onclick="javascript:$('#dg').edatagrid('saveRow')">Save</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-undo" plain="true" onclick="javascript:$('#dg').edatagrid('cancelRow')">Cancel</a>
</div>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 创建 CRUD 数据网格` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
