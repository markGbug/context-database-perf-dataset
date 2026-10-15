# jQuery EasyUI：jQuery EasyUI 数据网格 - 转换 HTML 表格为数据网格

- 来源：[jEasyUI 转换 HTML 表格为数据网格](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2860

## 本章内容

本实例演示如何转换表格（table）为数据网格（datagrid）。

数据网格（datagrid）的列信息是定义在 <thead> 标记中，数据是定义在 <tbody> 标记中。确保为所有的数据列设置 field 名称，请看下面的实例：

```html
    <table id="tt" class="easyui-datagrid" style="width:400px;height:auto;">
        <thead>
            <tr>
                <th field="name1" width="50">Col 1</th>
                <th field="name2" width="50">Col 2</th>
                <th field="name3" width="50">Col 3</th>
                <th field="name4" width="50">Col 4</th>
                <th field="name5" width="50">Col 5</th>
                <th field="name6" width="50">Col 6</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
                <td>Data 3</td>
                <td>Data 4</td>
                <td>Data 5</td>
                <td>Data 6</td>
            </tr>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
                <td>Data 3</td>
                <td>Data 4</td>
                <td>Data 5</td>
                <td>Data 6</td>
            </tr>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
                <td>Data 3</td>
                <td>Data 4</td>
                <td>Data 5</td>
                <td>Data 6</td>
            </tr>
            <tr>
                <td>Data 1</td>
                <td>Data 2</td>
                <td>Data 3</td>
                <td>Data 4</td>
                <td>Data 5</td>
                <td>Data 6</td>
            </tr>
        </tbody>
    </table>
```

非常棒，您可以定义一个复杂的表头，例如：

```html
    <thead>
        <tr>
            <th field="name1" width="50" rowspan="2">Col 1</th>
            <th field="name2" width="50" rowspan="2">Col 2</th>
            <th field="name3" width="50" rowspan="2">Col 3</th>
            <th colspan="3">Details</th>
        </tr>
        <tr>
            <th field="name4" width="50">Col 4</th>
            <th field="name5" width="50">Col 5</th>
            <th field="name6" width="50">Col 6</th>
        </tr>
    </thead>
```

现在您可以看见，复杂表头已经创建。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid1.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 转换 HTML 表格为数据网格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
