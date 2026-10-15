# MongoDB：MongoDB 备份(mongodump)与恢复(mongorestore)

- 来源：[MongoDB 备份与恢复](https://www.runoob.com/mongodb/mongodb-mongodump-mongorestore.html)
- 分类：数据库
- 技术：MongoDB
- 笔记类型：练习笔记
- 章节序号：1485

## 本章内容

## MongoDB数据备份

在Mongodb中我们使用mongodump命令来备份MongoDB数据。该命令可以导出所有数据到指定目录中。

mongodump命令可以通过参数指定导出的数据量级转存的服务器。


### 语法

mongodump命令脚本语法如下：

```text
>mongodump -h dbhost -d dbname -o dbdirectory
```

- -h：MongoDB 所在服务器地址，例如：127.0.0.1，当然也可以指定端口号：127.0.0.1:27017
- -d：需要备份的数据库实例，例如：test
- -o：备份的数据存放位置，例如：c:\data\dump，当然该目录需要提前建立，在备份完成后，系统自动在dump目录下建立一个test目录，这个目录里面存放该数据库实例的备份数据。


### 实例

在本地使用 27017 启动你的mongod服务。打开命令提示符窗口，进入MongoDB安装目录的bin目录输入命令mongodump:

```text
>mongodump
```

执行以上命令后，客户端会连接到ip为 127.0.0.1 端口号为 27017 的MongoDB服务上，并备份所有数据到 bin/dump/ 目录中。命令输出结果如下：

mongodump 命令可选参数列表如下所示：


## MongoDB数据恢复

mongodb使用 mongorestore 命令来恢复备份的数据。


### 语法

mongorestore命令脚本语法如下：

```html
>mongorestore -h <hostname><:port> -d dbname <path>
```

- --host <:port>, -h <:port>：MongoDB所在服务器地址，默认为： localhost:27017
- --db , -d ：需要恢复的数据库实例，例如：test，当然这个名称也可以和备份时候的不一样，比如test2
- --drop：恢复的时候，先删除当前数据，然后恢复备份的数据。就是说，恢复后，备份后添加修改的数据都会被删除，慎用哦！
- <path>： mongorestore 最后的一个参数，设置备份数据所在位置，例如：c:\data\dump\test。 你不能同时指定 <path> 和 --dir 选项，--dir也可以设置备份目录。
- --dir：指定备份的目录 你不能同时指定 <path> 和 --dir 选项。

接下来我们执行以下命令:

```text
>mongorestore
```

执行以上命令输出结果如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MongoDB 备份与恢复` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
