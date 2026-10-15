# jQuery EasyUI：jQuery EasyUI 菜单与按钮 - 创建简单的菜单

- 来源：[jEasyUI 创建简单的菜单](https://www.runoob.com/jeasyui/jeasyui-mb-menu.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2849

## 本章内容

菜单（Menu）定义在一些 DIV 标记中，如下所示：

```html
    <div id="mm" class="easyui-menu" style="width:120px;">
        <div onclick="javascript:alert('new')">New</div>
        <div>
            <span>Open</span>
            <div style="width:150px;">
                <div><b>Word</b></div>
                <div>Excel</div>
                <div>PowerPoint</div>
            </div>
        </div>
        <div icon="icon-save">Save</div>
        <div class="menu-sep"></div>
        <div>Exit</div>
    </div>
```

当菜单创建之后是不显示的，调用 'show' 方法显示它或者调用 'hide' 方法隐藏它：

```text
    $('#mm').menu('show', {
      left: 200,
      top: 100
    });
```


## 下载 jQuery EasyUI 实例

jeasyui-mb-menu.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建简单的菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
