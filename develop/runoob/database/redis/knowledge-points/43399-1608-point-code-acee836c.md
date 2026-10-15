# 知识点 43399：Redis：Redis 脚本 - 实例

- 来源：[Redis 脚本](https://www.runoob.com/redis/redis-scripting.html)
- 来源章节：[1608-redis-scripting-study.md](../chapters/1608-redis-scripting-study.md)
- 分类：数据库
- 技术：Redis
- 所在小节：实例
- 知识类型：代码
- 原章节序号：1608

## 原文片段

```text
redis 127.0.0.1:6379> EVAL "return {KEYS[1],KEYS[2],ARGV[1],ARGV[2]}" 2 key1 key2 first second

1) "key1"
2) "key2"
3) "first"
4) "second"
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `Redis 脚本` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
