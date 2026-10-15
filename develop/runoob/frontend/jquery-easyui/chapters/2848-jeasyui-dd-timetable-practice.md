# jQuery EasyUI：jQuery EasyUI 拖放 - 创建学校课程表

- 来源：[jEasyUI 创建学校课程表](https://www.runoob.com/jeasyui/jeasyui-dd-timetable.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2848

## 本章内容

本教程将向您展示如何使用 jQuery EasyUI 创建一个学校课程表。 我们将创建两个表格：在左侧显示学校科目，在右侧显示时间表。 您可以拖动学校科目并放置到时间表单元格上。 学校科目是一个 <div class="item"> 元素，时间表单元格是一个 <td class="drop"> 元素。

```html
    <div class="left">
        <table>
            <tr>
                <td><div class="item">English</div></td>
            </tr>
            <tr>
                <td><div class="item">Science</div></td>
            </tr>
            <!-- other subjects -->
        </table>
    </div>
```

```html
    <div class="right">
        <table>
            <tr>
                <td class="blank"></td>
                <td class="title">Monday</td>
                <td class="title">Tuesday</td>
                <td class="title">Wednesday</td>
                <td class="title">Thursday</td>
                <td class="title">Friday</td>
            </tr>
            <tr>
                <td class="time">08:00</td>
                <td class="drop"></td>
                <td class="drop"></td>
                <td class="drop"></td>
                <td class="drop"></td>
                <td class="drop"></td>
            </tr>
            <!-- other cells -->
        </table>
    </div>
```

```text
    $('.left .item').draggable({
        revert:true,
        proxy:'clone'
    });
```

```javascript
    $('.right td.drop').droppable({
        onDragEnter:function(){
            $(this).addClass('over');
        },
        onDragLeave:function(){
            $(this).removeClass('over');
        },
        onDrop:function(e,source){
            $(this).removeClass('over');
            if ($(source).hasClass('assigned')){
                $(this).append(source);
            } else {
                var c = $(source).clone().addClass('assigned');
                $(this).empty().append(c);
                c.draggable({
                    revert:true
                });
            }
        }
    });
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建学校课程表` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
