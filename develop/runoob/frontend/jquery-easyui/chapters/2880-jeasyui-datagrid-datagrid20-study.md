# jQuery EasyUI：jQuery EasyUI 数据网格 - 创建属性网格

- 来源：[jEasyUI 创建属性网格](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid20.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2880

## 本章内容

属性网格（property grid）带有一个内置的 expand（展开）/collapse（合并） 按钮，可以简单地为行分组。您可以简单地创建一个可编辑属性的分层（hierarchical）列表。

```html
    <table id="tt" class="easyui-propertygrid" style="width:300px"
            url="propertygrid_data.json"
            showGroup="true" scrollbarSize="0"
    ></table>
```

```text
    [
        {"name":"Name","value":"Bill Smith","group":"ID Settings","editor":"text"},
        {"name":"Address","value":"","group":"ID Settings","editor":"text"},
        {"name":"Age","value":"40","group":"ID Settings","editor":"numberbox"},
        {"name":"Birthday","value":"01/02/2012","group":"ID Settings","editor":"datebox"},
        {"name":"SSN","value":"123-456-7890","group":"ID Settings","editor":"text"},
        {"name":"Email","value":"bill@gmail.com","group":"Marketing Settings","editor":{
            "type":"validatebox",
            "options":{
                "validType":"email"
            }
        }},
        {"name":"FrequentBuyer","value":"false","group":"Marketing Settings","editor":{
            "type":"checkbox",
            "options":{
                "on":true,
                "off":false
            }
        }}
    ]
```

正如您所看到的，属性网格（property grid）的创建不需要任何的 javascript 代码。您可以简单地继承扩展 editor 类型。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid20.zip


## 复习重点

- 能说明 `jEasyUI 创建属性网格` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
