# jQuery EasyUI：jQuery EasyUI 树形菜单 - 使用标记创建树形菜单

- 来源：[jEasyUI 使用标记创建树形菜单](https://www.runoob.com/jeasyui/jeasyui-tree-tree1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2890

## 本章内容

一个树形菜单（Tree）可以从标记创建。easyui 树形菜单（Tree）也可以定义在 <ul> 元素中。无序列表的 <ul> 元素提供一个基础的树（Tree）结构。每一个 <li> 元素将产生一个树节点，子 <ul> 元素将产生一个父树节点。

```html
    <ul class="easyui-tree">
        <li>
            <span>Folder</span>
            <ul>
                <li>
                    <span>Sub Folder 1</span>
                    <ul>
                        <li><span>File 11</span></li>
                        <li><span>File 12</span></li>
                        <li><span>File 13</span></li>
                    </ul>
                </li>
                <li><span>File 2</span></li>
                <li><span>File 3</span></li>
            </ul>
        </li>
        <li><span>File21</span></li>
    </ul>
```


## 下载 jQuery EasyUI 实例

jeasyui-tree-tree1.zip


## 复习重点

- 能说明 `jEasyUI 使用标记创建树形菜单` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
