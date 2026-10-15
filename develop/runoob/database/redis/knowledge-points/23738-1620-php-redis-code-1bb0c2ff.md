# 知识点 23738：Redis：PHP 使用 Redis - PHP安装redis扩展

- 来源：[PHP 使用 Redis](https://www.runoob.com/redis/redis-php.html)
- 来源章节：[1620-redis-php-study.md](../chapters/1620-redis-php-study.md)
- 分类：数据库
- 技术：Redis
- 所在小节：PHP安装redis扩展
- 知识类型：代码
- 原章节序号：1620

## 原文片段

```text
$ wget https://github.com/phpredis/phpredis/archive/3.1.4.tar.gz
$ tar zxvf 3.1.4.tar.gz                  # 解压
$ cd phpredis-3.1.4                      # 进入 phpredis 目录
$ /usr/local/php/bin/phpize              # php安装后的路径
$ ./configure --with-php-config=/usr/local/php/bin/php-config
$ make && make install
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `PHP安装redis扩展` 这一小节和 `PHP 使用 Redis` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
