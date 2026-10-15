# 知识点 26402：jQuery EasyUI：jEasyUI 格式化下拉框 - 本章内容

- 来源：[jEasyUI 格式化下拉框](https://www.runoob.com/jeasyui/jeasyui-form-form4.html)
- 来源章节：[2904-jeasyui-form-form4-study.md](../chapters/2904-jeasyui-form-form4-study.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2904

## 原文片段

```text
$('#cc').combobox({
        formatter:function(row){
            var imageFile = 'images/' + row.icon;
            return '<img class="item-img" src="'+imageFile+'"/><span class="item-text">'+row.text+'</span>';
        }
    });
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 格式化下拉框` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
