# Ruby：Ruby 连接 Mysql - MySql2

- 来源：[Ruby Mysql](https://www.runoob.com/ruby/ruby-mysql-mysql2.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3742

## 本章内容

前面一章节我们介绍了 Ruby DBI 的使用。这章节我们技术 Ruby 连接 Mysql 更高效的驱动 mysql2，目前也推荐使用这种方式连接 MySql。

安装 mysql2 驱动：

```text
gem install mysql2
```

你需要使用 –with-mysql-config 配置 mysql_config 的路径，如： –with-mysql-config=/some/random/path/bin/mysql_config。


### 连接

连接数据库语法如下：

```text
client = Mysql2::Client.new(:host => "localhost", :username => "root")
```

更多参数可以查看 http://api.rubyonrails.org/classes/ActiveRecord/ConnectionAdapters/MysqlAdapter.html。


### 查询

```text
results = client.query("SELECT * FROM users WHERE group='githubbers'")
```


### 特殊字符转义

```text
escaped = client.escape("gi'thu\"bbe\0r's")
results = client.query("SELECT * FROM users WHERE group='#{escaped}'")
```

计算结果集返回的数量:

```text
results.count
```


### 迭代结果集：

```text
results.each do |row|
  # row 是哈希
  # 键值是数据库字段
  # 值都是对应 MySQL中数据
  puts row["id"] # row["id"].class == Fixnum
  if row["dne"]  # 不存在则是 nil
    puts row["dne"]
  end
end
```


## 实例

```text
#!/usr/bin/ruby -w
require 'mysql2'

client = Mysql2::Client.new(
    :host     => '127.0.0.1', # 主机
    :username => 'root',      # 用户名
    :password => '123456',    # 密码
    :database => 'test',      # 数据库
    :encoding => 'utf8'       # 编码
    )
results = client.query("SELECT VERSION()")
results.each do |row|
  puts row
end
```

以上实例运行输出结果为：

```text
{"VERSION()"=>"5.6.21"}
```


### 连接选项

```text
Mysql2::Client.new(
  :host,
  :username,
  :password,
  :port,
  :database,
  :socket = '/path/to/mysql.sock',
  :flags = REMEMBER_OPTIONS | LONG_PASSWORD | LONG_FLAG | TRANSACTIONS | PROTOCOL_41 | SECURE_CONNECTION | MULTI_STATEMENTS,
  :encoding = 'utf8',
  :read_timeout = seconds,
  :write_timeout = seconds,
  :connect_timeout = seconds,
  :reconnect = true/false,
  :local_infile = true/false,
  :secure_auth = true/false,
  :default_file = '/path/to/my.cfg',
  :default_group = 'my.cfg section',
  :init_command => sql
  )
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby Mysql` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
