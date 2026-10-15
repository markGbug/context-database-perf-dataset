# jQuery EasyUI：jQuery EasyUI 表单 - 表单验证

- 来源：[jEasyUI 表单验证](https://www.runoob.com/jeasyui/jeasyui-form-form3.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2902

## 本章内容

本教程将向您展示如何验证一个表单。easyui 框架提供一个 validatebox 插件来验证一个表单。在本教程中，我们将创建一个联系表单，并应用 validatebox 插件来验证表单。然后您可以根据自己的需求来调整这个表单。

让我们创建一个简单的联系表单，带有 name、email、subject 和 message 字段：

```html
    <div style="padding:3px 2px;border-bottom:1px solid #ccc">Form Validation</div>
    <form id="ff" method="post">
        <div>
            <label for="name">Name:</label>
            <input class="easyui-validatebox" type="text" name="name" required="true"></input>
        </div>
        <div>
            <label for="email">Email:</label>
            <input class="easyui-validatebox" type="text" name="email" required="true" validType="email"></input>
        </div>
        <div>
            <label for="subject">Subject:</label>
            <input class="easyui-validatebox" type="text" name="subject" required="true"></input>
        </div>
        <div>
            <label for="message">Message:</label>
            <textarea name="message" style="height:60px;"></textarea>
        </div>
        <div>
            <input type="submit" value="Submit">
        </div>
    </form>
```

我们添加一个样式名为 easyui-validatebox 到 input 标记，所以 input 标记将根据 validType 属性应用验证。

当用户点击表单的 submit 按钮时，如果表单是无效的，我们应该阻止表单提交。

```text
    $('#ff').form({
        url:'form3_proc.php',
        onSubmit:function(){
            return $(this).form('validate');
        },
        success:function(data){
            $.messager.alert('Info', data, 'info');
        }
    });
```

如果表单是无效的，将显示一个提示信息。


## 下载 jQuery EasyUI 实例

jeasyui-form-form3.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 表单验证` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
