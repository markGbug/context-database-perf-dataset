# jQuery EasyUI：jQuery EasyUI 树形菜单 - 创建基础树形网格

- 来源：[jEasyUI 创建基础树形网格](https://www.runoob.com/jeasyui/jeasyui-tree-treegrid1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建基础树形网格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
