# 知识点 26341：jQuery EasyUI：jEasyUI 扩展编辑器 - 本章内容

- 来源：[jEasyUI 扩展编辑器](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid23.html)
- 来源章节：[2874-jeasyui-datagrid-datagrid23-practice.md](../chapters/2874-jeasyui-datagrid-datagrid23-practice.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2874

## 原文片段

```text
<table id="tt" style="width:600px;height:250px"
            url="data/datagrid_data.json" title="Editable DataGrid" iconCls="icon-edit"
            singleSelect="true" idField="itemid" fitColumns="true">
        <thead>
            <tr>
                <th field="itemid" width="60">Item ID</th>
                <th field="listprice" width="80" align="right" editor="{type:'numberbox',options:{precision:1}}">List Price</th>
                <th field="unitcost" width="80" align="right" editor="numberspinner">Unit Cost</th>
                <th field="attr1" width="180" editor="text">Attribute</th>
                <th field="status" width="60" align="center" editor="{type:'checkbox',options:{on:'P',off:''}}">Status</th>
                <th field="action" width="80" align="center" formatter="formatAction">Action</th>
            </tr>
        </thead>
    </table>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 扩展编辑器` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
