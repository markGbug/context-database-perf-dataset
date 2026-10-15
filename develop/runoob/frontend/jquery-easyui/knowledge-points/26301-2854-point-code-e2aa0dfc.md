# 知识点 26301：jQuery EasyUI：jEasyUI 创建复杂布局 - 本章内容

- 来源：[jEasyUI 创建复杂布局](https://www.runoob.com/jeasyui/jeasyui-layout-panel.html)
- 来源章节：[2854-jeasyui-layout-panel-practice.md](../chapters/2854-jeasyui-layout-panel-practice.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2854

## 原文片段

```text
<div class="easyui-panel" title="Complex Panel Layout" iconCls="icon-search" collapsible="true" style="padding:5px;width:500px;height:250px;">
        <div class="easyui-layout" fit="true">
            <div region="north" border="false" class="p-search">
                <label>Search:</label><input></input>
            </div>
            <div region="center" border="false">
                <div class="easyui-layout" fit="true">
                    <div region="east" border="false" class="p-right">
                        <img src="images/msn.gif"/>
                    </div>
                    <div region="center" border="false" style="border:1px solid #ccc;">
                        <div class="easyui-layout" fit="true">
                            <div region="south" split="true" border="false" style="height:60px;">
                                <textarea style="border:0;width:100%;height:100%;resize:none">Hi,I am easyui.</textarea>
                            </div>
                            <div region="center" border="false">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 创建复杂布局` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
