# jQuery：jQuery 树型菜单插件(Treeview)

- 来源：[jQuery Treeview](https://www.runoob.com/jquery/jquery-plugin-treeview.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：3009

## 本章内容

jQuery Treeview 提供了一个无序灵活的可折叠的树形菜单。适用于一些菜单的导航，支持基于 cookie 的持久性菜单。

```html
<ul id="browser" class="filetree treeview-famfamfam">
    <li><span class="folder">Folder 1</span>
        <ul>
            <li><span class="folder">Item 1.1</span>
                <ul>
                    <li><span class="file">Item 1.1.1</span></li>
                </ul>
            </li>
            <li><span class="folder">Folder 2</span>
                <ul>
                    <li><span class="folder">Subfolder 2.1</span>
                        <ul id="folder21">
                            <li><span class="file">File 2.1.1</span></li>
                            <li><span class="file">File 2.1.2</span></li>
                        </ul>
                    </li>
                    <li><span class="folder">Subfolder 2.2</span>
                        <ul>
                            <li><span class="file">File 2.2.1</span></li>
                            <li><span class="file">File 2.2.2</span></li>
                        </ul>
                    </li>
                </ul>
            </li>
            <li class="closed"><span class="folder">Folder 3 (closed at start)</span>
                <ul>
                    <li><span class="file">File 3.1</span></li>
                </ul>
            </li>
            <li><span class="file">File 4</span></li>
        </ul>
    </li>
</ul>
```

尝试一下 »


## 相关链接

jQuery Treeview 完整实例下载：http://static.jyshare.com/download/jquery-treeview.zip。

jQuery Treeview Github 地址：https://github.com/jzaefferer/jquery-treeview。


## 复习重点

- 能说明 `jQuery Treeview` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
