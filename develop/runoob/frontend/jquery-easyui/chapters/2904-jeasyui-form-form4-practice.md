# jQuery EasyUI：jQuery EasyUI 表单 - 格式化下拉框

- 来源：[jEasyUI 格式化下拉框](https://www.runoob.com/jeasyui/jeasyui-form-form4.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2904

## 本章内容

本教程向您展示如何创建一个简单的下拉框（Combobox），让它在下拉框中显示图片项。您可以在下拉框（combobox）上使用 formatter 函数来告诉它如何格式化每一个条目。

```html
    <input id="cc" style="width:100px"
            url="data/combobox_data.json"
            valueField="id" textField="text">
    </input>
```

```html
    $('#cc').combobox({
        formatter:function(row){
            var imageFile = 'images/' + row.icon;
            return '<img class="item-img" src="'+imageFile+'"/><span class="item-text">'+row.text+'</span>';
        }
    });
```


## 下载 jQuery EasyUI 实例

jeasyui-form-form4.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 格式化下拉框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
