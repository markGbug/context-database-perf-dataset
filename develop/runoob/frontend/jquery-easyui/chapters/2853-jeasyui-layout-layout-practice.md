# jQuery EasyUI：jQuery EasyUI 布局 - 为网页创建边框布局

- 来源：[jEasyUI 创建边框布局](https://www.runoob.com/jeasyui/jeasyui-layout-layout.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2853

## 本章内容

边框布局（border layout）提供五个区域：east、west、north、south、center。以下是一些通常用法：

- north 区域可以用来显示网站的标语。
- south 区域可以用来显示版权以及一些说明。
- west 区域可以用来显示导航菜单。
- east 区域可以用来显示一些推广的项目。
- center 区域可以用来显示主要的内容。

为了应用布局（layout），您应该确定一个布局（layout）容器，然后定义一些区域。布局（layout）必须至少需要一个 center 区域，以下是一个布局（layout）实例：

```html
    <div class="easyui-layout" style="width:400px;height:200px;">
        <div region="west" split="true" title="Navigator" style="width:150px;">
            <p style="padding:5px;margin:0;">Select language:</p>
            <ul>
                <li><a href="javascript:void(0)" onclick="showcontent('java')">Java</a></li>
                <li><a href="javascript:void(0)" onclick="showcontent('cshape')">C#</a></li>
                <li><a href="javascript:void(0)" onclick="showcontent('vb')">VB</a></li>
                <li><a href="javascript:void(0)" onclick="showcontent('erlang')">Erlang</a></li>
            </ul>
        </div>
        <div id="content" region="center" title="Language" style="padding:5px;">
        </div>
    </div>
```

我们在一个 <div> 容器中创建了一个边框布局（border layout），布局（layout）把容器切割为两个部分，左边是导航菜单，右边是主要内容。

最后我们写一个 onclick 事件处理函数来检索数据，'showcontent' 函数非常简单：

```javascript
    function showcontent(language){
        $('#content').html('Introduction to ' + language + ' language');
    }
```


## 下载 jQuery EasyUI 实例

jeasyui-layout-layout.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建边框布局` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
