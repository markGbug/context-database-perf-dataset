# jQuery EasyUI：jQuery EasyUI 表单 - 创建异步提交表单

- 来源：[jEasyUI 创建异步提交表单](https://www.runoob.com/jeasyui/jeasyui-form-form1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2901

## 本章内容

本教程向您展示如何通过 easyui 提交一个表单（Form）。我们创建一个带有 name、email 和 phone 字段的表单。通过使用 easyui 表单（form）插件来改变表单（form）为 ajax 表单（form）。表单（form）提交所有字段到后台服务器，服务器处理和发送一些数据返回到前端页面。我们接收返回数据，并将它显示出来。

```html
    <div style="padding:3px 2px;border-bottom:1px solid #ccc">Ajax Form</div>
    <form id="ff" action="form1_proc.php" method="post">
        <table>
            <tr>
                <td>Name:</td>
                <td><input name="name" type="text"></input></td>
            </tr>
            <tr>
                <td>Email:</td>
                <td><input name="email" type="text"></input></td>
            </tr>
            <tr>
                <td>Phone:</td>
                <td><input name="phone" type="text"></input></td>
            </tr>
            <tr>
                <td></td>
                <td><input type="submit" value="Submit"></input></td>
            </tr>
        </table>
    </form>
```

```text
    $('#ff').form({
        success:function(data){
            $.messager.alert('Info', data, 'info');
        }
    });
```

```html
    $name = $_POST['name'];
    $email = $_POST['email'];
    $phone = $_POST['phone'];

    echo "Your Name: $name <br/> Your Email: $email <br/> Your Phone: $phone";
```


## 下载 jQuery EasyUI 实例

jeasyui-form-form1.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建异步提交表单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
