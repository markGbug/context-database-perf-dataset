# jQuery EasyUI：jQuery EasyUI 窗口 - 创建简单窗口

- 来源：[jEasyUI 创建简单窗口](https://www.runoob.com/jeasyui/jeasyui-win-win1.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2885

## 本章内容

创建一个窗口（window）非常简单，我们创建一个 DIV 标记：

```html
<div id="win" class="easyui-window" title="My Window" style="width:300px;height:100px;padding:5px;">
    Some Content.
</div>
```

现在运行测试页面，您会看见一个窗口（window）显示在您的屏幕上。我们不需要写任何的 javascript 代码。

如果您希望创建一个隐藏的窗口（window），记得设置 'closed' 属性为 'true' 值，您可以调用 'open' 方法来打开窗口（window）：

```html
<div id="win" class="easyui-window" title="My Window" closed="true" style="width:300px;height:100px;padding:5px;">
    Some Content.
</div>
```

```text
$('#win').window('open');
```

作为最后的实例演示，我们创建一个登录窗口（window）：

```html
<div id="win" class="easyui-window" title="Login" style="width:300px;height:180px;">
    <form style="padding:10px 20px 10px 40px;">
        <p>Name: <input type="text"></p>
        <p>Pass: <input type="password"></p>
        <div style="padding:5px;text-align:center;">
            <a href="#" class="easyui-linkbutton" icon="icon-ok">Ok</a>
            <a href="#" class="easyui-linkbutton" icon="icon-cancel">Cancel</a>
        </div>
    </form>
</div>
```


## 下载 jQuery EasyUI 实例

jeasyui-win-win1.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建简单窗口` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
