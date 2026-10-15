# MongoDB：MongoDB PHP

- 来源：[MongoDB PHP](https://www.runoob.com/mongodb/mongodb-php.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1489

## 本章内容

在php中使用mongodb你必须使用 mongodb 的 php驱动。

MongoDB PHP在各平台上的安装及驱动包下载请查看:PHP安装MongoDB扩展驱动

如果你使用的是 PHP7，请参阅：PHP7 MongoDB 安装与使用。


## 确保连接及选择一个数据库

为了确保正确连接，你需要指定数据库名，如果数据库在mongoDB中不存在，mongoDB会自动创建

代码片段如下：

```text
<?php
$m = new MongoClient(); // 连接默认主机和端口为：mongodb://localhost:27017
$db = $m->test; // 获取名称为 "test" 的数据库
?>
```


## 创建集合

创建集合的代码片段如下：

```text
<?php
$m = new MongoClient(); // 连接
$db = $m->test; // 获取名称为 "test" 的数据库
$collection = $db->createCollection("runoob");
echo "集合创建成功";
?>
```

执行以上程序，输出结果如下：

```text
集合创建成功
```


## 插入文档

在mongoDB中使用 insert() 方法插入文档：

插入文档代码片段如下：

```text
<?php
$m = new MongoClient();    // 连接到mongodb
$db = $m->test;            // 选择一个数据库
$collection = $db->runoob; // 选择集合
$document = array(
    "title" => "MongoDB",
    "description" => "database",
    "likes" => 100,
    "url" => "http://www.runoob.com/mongodb/",
    "by", "菜鸟教程"
);
$collection->insert($document);
echo "数据插入成功";
?>
```

执行以上程序，输出结果如下：

```text
数据插入成功
```

然后我们在 mongo 客户端使用 db.runoob.find().pretty(); 命令查看数据：


## 查找文档

使用find() 方法来读取集合中的文档。

读取使用文档的代码片段如下：

```text
<?php
$m = new MongoClient();    // 连接到mongodb
$db = $m->test;            // 选择一个数据库
$collection = $db->runoob; // 选择集合

$cursor = $collection->find();
// 迭代显示文档标题
foreach ($cursor as $document) {
    echo $document["title"] . "\n";
}
?>
```

执行以上程序，输出结果如下：

```text
MongoDB
```


## 更新文档

使用 update() 方法来更新文档。

以下实例将更新文档中的标题为' MongoDB 教程'， 代码片段如下：

```html
<pre>
<?php
$m = new MongoClient();    // 连接到mongodb
$db = $m->test;            // 选择一个数据库
$collection = $db->runoob; // 选择集合
// 更新文档
$collection->update(array("title"=>"MongoDB"), array('$set'=>array("title"=>"MongoDB 教程")));
// 显示更新后的文档
$cursor = $collection->find();
// 循环显示文档标题
foreach ($cursor as $document) {
    echo $document["title"] . "\n";
}
?>
```

执行以上程序，输出结果如下：

```text
MongoDB 教程
```

然后我们在 mongo 客户端使用 db.runoob.find().pretty(); 命令查看数据：


## 删除文档

使用 remove() 方法来删除文档。

以下实例中我们将移除 'title' 为 'MongoDB 教程' 的一条数据记录。， 代码片段如下：

```text
<?php
$m = new MongoClient();    // 连接到mongodb
$db = $m->test;            // 选择一个数据库
$collection = $db->runoob; // 选择集合

// 移除文档
$collection->remove(array("title"=>"MongoDB 教程"), array("justOne" => true));

// 显示可用文档数据
$cursor = $collection->find();
foreach ($cursor as $document) {
    echo $document["title"] . "\n";
}
?>
```

除了以上实例外，在php中你还可以使用findOne(), save(), limit(), skip(), sort()等方法来操作Mongodb数据库。

更多的操作方法可以参考 Mongodb 核心类：http://php.net/manual/zh/mongo.core.php。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB PHP` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
