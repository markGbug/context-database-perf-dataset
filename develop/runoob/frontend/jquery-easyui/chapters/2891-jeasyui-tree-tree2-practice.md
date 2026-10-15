# jQuery EasyUI：jQuery EasyUI 树形菜单 - 创建异步树形菜单

- 来源：[jEasyUI 创建异步树形菜单](https://www.runoob.com/jeasyui/jeasyui-tree-tree2.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2891

## 本章内容

为了创建异步的树形菜单（Tree），每一个树节点必须要有一个 'id' 属性，这个将提交回服务器去检索子节点数据。

```html
    <ul id="tt" class="easyui-tree"
            url="tree2_getdata.php">
    </ul>
```

```java
    $id = isset($_POST['id']) ? intval($_POST['id']) : 0;

    include 'conn.php';

    $result = array();
    $rs = mysql_query("select * from nodes where parentId=$id");
    while($row = mysql_fetch_array($rs)){
        $node = array();
        $node['id'] = $row['id'];
        $node['text'] = $row['name'];
        $node['state'] = has_child($row['id']) ? 'closed' : 'open';
        array_push($result,$node);
    }

    echo json_encode($result);

    function has_child($id){
        $rs = mysql_query("select count(*) from nodes where parentId=$id");
        $row = mysql_fetch_array($rs);
        return $row[0] > 0 ? true : false;
    }
```


## 下载 jQuery EasyUI 实例

jeasyui-tree-tree2.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建异步树形菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
