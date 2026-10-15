# jQuery EasyUI：jQuery EasyUI 树形菜单 - 创建复杂树形网格

- 来源：[jEasyUI 创建复杂树形网格](https://www.runoob.com/jeasyui/jeasyui-tree-treegrid2.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2897

## 本章内容

树形网格（TreeGrid）可以展示有限空间上带有多列和复杂数据电子表格。本教程将演示如何将表格数据排列在分割的网格和多行表头中，以便组织共同的数据。

```html
    <table title="Complex TreeGrid" class="easyui-treegrid" style="width:550px;height:250px"
            url="data/treegrid2_data.json"
            rownumbers="true" showFooter="true"
            idField="id" treeField="region">
        <thead frozen="true">
            <tr>
                <th field="region" width="150">Region</th>
            </tr>
        </thead>
        <thead>
            <tr>
                <th colspan="4">2009</th>
                <th colspan="4">2010</th>
            </tr>
            <tr>
                <th field="f1" width="50" align="right">1st qrt.</th>
                <th field="f2" width="50" align="right">2st qrt.</th>
                <th field="f3" width="50" align="right">3st qrt.</th>
                <th field="f4" width="50" align="right">4st qrt.</th>
                <th field="f5" width="50" align="right">1st qrt.</th>
                <th field="f6" width="50" align="right">2st qrt.</th>
                <th field="f7" width="50" align="right">3st qrt.</th>
                <th field="f8" width="50" align="right">4st qrt.</th>
            </tr>
        </thead>
    </table>
```

正如您所看到的，树形网格（Treegrid）的使用和数据网格（Datagrid）一样。请使用 'frozen' 属性来定义冻结列，列的 'colspan' 和 'rowspan' 属性来定义多行表头。


## 下载 jQuery EasyUI 实例

jeasyui-tree-treegrid2.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建复杂树形网格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
