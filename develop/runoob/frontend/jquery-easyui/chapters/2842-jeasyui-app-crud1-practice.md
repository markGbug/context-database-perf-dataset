# jQuery EasyUI：jQuery EasyUI 应用 - 创建 CRUD 应用

- 来源：[jEasyUI 创建 CRUD 应用](https://www.runoob.com/jeasyui/jeasyui-app-crud1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2842

## 本章内容

数据收集并妥善管理数据是网络应用共同的必要。CRUD 允许我们生成页面列表，并编辑数据库记录。本教程将向你演示如何使用 jQuery EasyUI 框架实现一个 CRUD DataGrid。

我们将使用下面的插件：

- datagrid：向用户展示列表数据。
- dialog：创建或编辑一条单一的用户信息。
- form：用于提交表单数据。
- messager：显示一些操作信息。

我们将使用 MySql 数据库来存储用户信息。创建数据库和 'users' 表。

创建没有 javascript 代码的 DataGrid。

```html
<table id="dg" title="My Users" class="easyui-datagrid" style="width:550px;height:250px"
        url="get_users.php"
        toolbar="#toolbar"
        rownumbers="true" fitColumns="true" singleSelect="true">
    <thead>
        <tr>
            <th field="firstname" width="50">First Name</th>
            <th field="lastname" width="50">Last Name</th>
            <th field="phone" width="50">Phone</th>
            <th field="email" width="50">Email</th>
        </tr>
    </thead>
</table>
<div id="toolbar">
    <a href="#" class="easyui-linkbutton" iconCls="icon-add" plain="true" onclick="newUser()">New User</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-edit" plain="true" onclick="editUser()">Edit User</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-remove" plain="true" onclick="destroyUser()">Remove User</a>
</div>
```

我们不需要写任何的 javascript 代码，就能向用户显示列表，如下图所示：

DataGrid 使用 'url' 属性，并赋值为 'get_users.php'，用来从服务器检索数据。

get_users.php 文件的代码

```java
$rs = mysql_query('select * from users');
$result = array();
while($row = mysql_fetch_object($rs)){
    array_push($result, $row);
}

echo json_encode($result);
```

我们使用相同的对话框来创建或编辑用户。

```html
<div id="dlg" class="easyui-dialog" style="width:400px;height:280px;padding:10px 20px"
        closed="true" buttons="#dlg-buttons">
    <div class="ftitle">User Information</div>
    <form id="fm" method="post">
        <div class="fitem">
            <label>First Name:</label>
            <input name="firstname" class="easyui-validatebox" required="true">
        </div>
        <div class="fitem">
            <label>Last Name:</label>
            <input name="lastname" class="easyui-validatebox" required="true">
        </div>
        <div class="fitem">
            <label>Phone:</label>
            <input name="phone">
        </div>
        <div class="fitem">
            <label>Email:</label>
            <input name="email" class="easyui-validatebox" validType="email">
        </div>
    </form>
</div>
<div id="dlg-buttons">
    <a href="#" class="easyui-linkbutton" iconCls="icon-ok" onclick="saveUser()">Save</a>
    <a href="#" class="easyui-linkbutton" iconCls="icon-cancel" onclick="javascript:$('#dlg').dialog('close')">Cancel</a>
</div>
```

这个对话框已经创建，也没有任何的 javascript 代码:。

当创建用户时，打开一个对话框并清空表单数据。

```javascript
function newUser(){
    $('#dlg').dialog('open').dialog('setTitle','New User');
    $('#fm').form('clear');
    url = 'save_user.php';
}
```


## 下载 jQuery EasyUI 实例

jeasyui-app-crud1.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建 CRUD 应用` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
