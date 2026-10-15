# 知识点 26324：jQuery EasyUI：jEasyUI 设置冻结列 - 本章内容

- 来源：[jEasyUI 设置冻结列](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid5.html)
- 来源章节：[2865-jeasyui-datagrid-datagrid5-study.md](../chapters/2865-jeasyui-datagrid-datagrid5-study.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2865

## 原文片段

```text
$('#tt').datagrid({
        title:'Frozen Columns',
        iconCls:'icon-save',
        width:500,
        height:250,
        url:'data/datagrid_data.json',
        frozenColumns:[[
            {field:'itemid',title:'Item ID',width:80},
            {field:'productid',title:'Product ID',width:80},
        ]],
        columns:[[
            {field:'listprice',title:'List Price',width:80,align:'right'},
            {field:'unitcost',title:'Unit Cost',width:80,align:'right'},
            {field:'attr1',title:'Attribute',width:100},
            {field:'status',title:'Status',width:60}
        ]]
    });
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 设置冻结列` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
