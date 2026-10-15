# PHP：PHP PDO

- 来源：[PHP PDO](https://www.runoob.com/php/php-pdo.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：学习笔记
- 章节序号：1120

## 本章内容

PHP 数据对象 （PDO） 扩展为PHP访问数据库定义了一个轻量级的一致接口。

PDO 提供了一个数据访问抽象层，这意味着，不管使用哪种数据库，都可以用相同的函数（方法）来查询和获取数据。

PDO随PHP5.1发行，在PHP5.0的PECL扩展中也可以使用，无法运行于之前的PHP版本。


## PDO 安装

你可以通过 PHP 的 phpinfo() 函数来查看是否安装了PDO扩展。


### 在 Unix 系统上安装 PDO

在Unix上或Linux上你需要添加以下扩展：

```text
extension=pdo.so
```


### Windows 用户

PDO 和所有主要的驱动作为共享扩展随 PHP 一起发布，要激活它们只需简单地编辑 php.ini 文件，并添加以下扩展：

```text
extension=php_pdo.dll
```

```text
;extension=php_pdo_firebird.dll
;extension=php_pdo_informix.dll
;extension=php_pdo_mssql.dll
;extension=php_pdo_mysql.dll
;extension=php_pdo_oci.dll
;extension=php_pdo_oci8.dll
;extension=php_pdo_odbc.dll
;extension=php_pdo_pgsql.dll
;extension=php_pdo_sqlite.dll
```

在设定好这些配置后，我们需要重启PHP 或 Web服务器。

接下来我们们来看下具体的实例，以下为使用PDO连接MySql数据库的实例：


## 实例

很简单吧，接下来就让我们来具体看下PHP PDO具体说明：

- 预定义常量
- PHP PDO连接连接管理
- PHP PDO 事务与自动提交
- PHP PDO 预处理语句与存储过程
- PHP PDO 错误与错误处理


## 复习重点

- 能说明 `PHP PDO` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
