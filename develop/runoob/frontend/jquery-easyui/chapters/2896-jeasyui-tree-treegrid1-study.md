# jQuery EasyUI：jQuery EasyUI 树形菜单 - 创建基础树形网格

- 来源：[jEasyUI 创建基础树形网格](https://www.runoob.com/jeasyui/jeasyui-tree-treegrid1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2896

## 本章内容

树形网格（TreeGrid）组件从数据网格（DataGrid）继承，但是允许在行之间存在父/子节点关系。许多属性继承至数据网格（DataGrid），可以用在树形网格（TreeGrid）中。为了使用树形网格（TreeGrid），用户必须定义 'treeField' 属性，指明哪个字段作为树节点。

本教程将向您展示如何使用树形网格（TreeGrid）组件设置一个文件夹浏览。

```html
    <table id="test" title="Folder Browser" class="easyui-treegrid" style="width:400px;height:300px"
            url="data/treegrid_data.json"
            rownumbers="true"
            idField="id" treeField="name">
        <thead>
            <tr>
                <th field="name" width="160">Name</th>
                <th field="size" width="60" align="right">Size</th>
                <th field="date" width="100">Modified Date</th>
            </tr>
        </thead>
    </table>
```


## 下载 jQuery EasyUI 实例

jeasyui-tree-treegrid1.zip


## 复习重点

- 能说明 `jEasyUI 创建基础树形网格` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
