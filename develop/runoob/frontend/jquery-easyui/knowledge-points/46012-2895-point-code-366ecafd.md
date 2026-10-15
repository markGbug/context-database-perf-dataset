# 知识点 46012：jQuery EasyUI：jEasyUI 树形菜单加载父/子节点 - 本章内容

- 来源：[jEasyUI 树形菜单加载父/子节点](https://www.runoob.com/jeasyui/jeasyui-tree-tree6.html)
- 来源章节：[2895-jeasyui-tree-tree6-practice.md](../chapters/2895-jeasyui-tree-tree6-practice.md)
- 分类：前端开发
- 技术：jQuery EasyUI
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2895

## 原文片段

```text
function convert(rows){
        function exists(rows, parentId){
            for(var i=0; i<rows.length; i++){
                if (rows[i].id == parentId) return true;
            }
            return false;
        }

        var nodes = [];
        // get the top level nodes
        for(var i=0; i<rows.length; i++){
            var row = rows[i];
            if (!exists(rows, row.parentId)){
                nodes.push({
                    id:row.id,
                    text:row.name
                });
            }
        }

        var toDo = [];
        for(var i=0; i<nodes.length; i++){
            toDo.push(nodes[i]);
        }
        while(toDo.length){
            var node = toDo.shift();    // the parent node
            // get the children nodes
            for(var i=0; i<rows.length; i++){
                var row = rows[i];
                if (row.parentId == node.id){
                    var child = {id:row.id,text:row.name};
                    if (node.children){
                        node.children.push(child);
                    } else {
                        node.children = [child];
                    }
                    toDo.push(child);
                }
            }
        }
        return nodes;
    }
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `jEasyUI 树形菜单加载父/子节点` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
