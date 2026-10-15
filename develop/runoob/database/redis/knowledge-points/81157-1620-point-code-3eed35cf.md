# 知识点 81157：Redis：PHP 使用 Redis - 实例

- 来源：[PHP 使用 Redis](https://www.runoob.com/redis/redis-php.html)
- 来源章节：[1620-redis-php-practice.md](../chapters/1620-redis-php-practice.md)
- 分类：数据库
- 技术：Redis
- 所在小节：实例
- 知识类型：代码
- 原章节序号：1620

## 原文片段

```text
<?php
//连接本地的 Redis 服务
$redis = new Redis();
$redis->connect('127.0.0.1', 6379);
echo "Connection to server successfully";
//设置 redis 字符串数据
$redis->set("tutorial-name", "Redis tutorial");
// 获取存储的数据并输出
echo "Stored string in redis:: " . $redis->get("tutorial-name");
?>
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `PHP 使用 Redis` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
