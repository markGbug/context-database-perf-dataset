# R：R MySQL 连接

- 来源：[R MySQL 连接](https://www.runoob.com/r/r-mysql-connect.html)
- 分类：Python / 数据科学
- 技术：R
- 笔记类型：学习笔记
- 章节序号：4244

## 本章内容

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

如果你对 MySQL 还不了解，可以先查阅：MySQL 教程

R 语言读写 MySQL 文件需要安装扩展包，我们可以在 R 到控制台输入以下命令来安装：

```text
install.packages("RMySQL", repos = "https://mirrors.ustc.edu.cn/CRAN/")
```

查看是否安装成功：

```text
> any(grepl("RMySQL",installed.packages()))
[1] TRUE
```

MySQL 目前被甲骨文收购，所以很多人使用来它的复制版本 MariaDB，MariaDB 在 GNU GPL下开源，MariaDB 的开发是由 MySQL 的一些原始开发者领导的，所以语法操作都差不多：


## 复习重点

- 能说明 `R MySQL 连接` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
