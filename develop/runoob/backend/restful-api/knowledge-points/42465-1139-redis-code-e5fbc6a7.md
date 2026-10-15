# 知识点 42465：RESTful API：RESTful API 进阶 - Redis 缓存示例

- 来源：[RESTful API 进阶](https://www.runoob.com/restfulapi/restful-api-advance.html)
- 来源章节：[1139-restful-api-advance-study.md](../chapters/1139-restful-api-advance-study.md)
- 分类：后端开发
- 技术：RESTful API
- 所在小节：Redis 缓存示例
- 知识类型：代码
- 原章节序号：1139

## 原文片段

```text
// 缓存策略伪代码
async function getUser(userId) {
  // 1. 先检查缓存
  const cached = await redis.get(`user:${userId}`);
  if (cached) {
    return JSON.parse(cached);
  }

  // 2. 缓存未命中，查询数据库
  const user = await database.findUser(userId);

  // 3. 将结果缓存
  await redis.setex(`user:${userId}`, 3600, JSON.stringify(user));

  return user;
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `Redis 缓存示例` 这一小节和 `RESTful API 进阶` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
