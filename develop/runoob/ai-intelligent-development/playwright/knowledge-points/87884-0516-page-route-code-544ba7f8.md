# 知识点 87884：Playwright：Playwright 网络拦截 - 拦截请求：page.route()

- 来源：[Playwright 网络拦截](https://www.runoob.com/playwright/playwright-network-interception.html)
- 来源章节：[0516-playwright-network-interception-practice.md](../chapters/0516-playwright-network-interception-practice.md)
- 分类：AI / 智能开发
- 技术：Playwright
- 所在小节：拦截请求：page.route()
- 知识类型：代码
- 原章节序号：0516

## 原文片段

```text
await page.route('**/api/todos', async route => {
  // 拦截匹配的请求
  console.log('拦截到请求:', route.request().url());

  // 1. 直接放行（继续请求）
  await route.continue();

  // 2. 修改请求
  // await route.continue({ headers: { ...route.request().headers(), 'X-Test': 'true' } });

  // 3. 返回 mock 响应
  // await route.fulfill({
  //   status: 200,
  //   contentType: 'application/json',
  //   body: JSON.stringify([{ id: 1, text: 'mock todo', done: false }]),
  // });

  // 4. 拒绝请求
  // await route.abort();
});
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `拦截请求：page.route()` 这一小节和 `Playwright 网络拦截` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
