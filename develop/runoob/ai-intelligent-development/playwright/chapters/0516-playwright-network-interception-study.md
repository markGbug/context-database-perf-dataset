# Playwright：Playwright 网络拦截

- 来源：[Playwright 网络拦截](https://www.runoob.com/playwright/playwright-network-interception.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0516

## 本章内容

Playwright 的网络拦截 (Network Interception) 是自动化测试和爬虫场景中非常有用的能力，可以让我们拦截、修改、模拟网络请求与响应。

Playwright 提供了 page.route() 和 page.on('request') / page.on('response') 等 API，可以：

- 拦截请求：决定是否放行、修改 URL/headers/body、或者直接返回 mock 响应。
- 监听请求/响应：查看请求的 URL、方法、头部、响应状态码、响应体等。
- 模拟网络错误：阻止请求、返回错误码，测试应用的容错逻辑。

常见应用场景：

- Mock API：不用后端接口也能跑前端 UI 测试。
- 修改请求：比如加 token，测试异常 header。
- 性能调试：统计请求数、响应时间。
- 错误注入：模拟 500/404 等服务端异常。


### 拦截请求：page.route()

```javascript
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

参数说明：

- page.route(url, handler)：注册一个拦截器，url 支持字符串、正则或 ** 通配。
- route.request()：获取请求对象。
- route.continue([options])：放行请求，可以修改方法、headers、postData。
- route.fulfill(response)：直接返回伪造的响应。
- route.abort([errorCode])：中断请求，常见错误码如 "failed", "aborted", "timedout"。


### 监听请求和响应

```javascript
// 监听所有请求
page.on('request', req => {
  console.log(`➡️ 请求: ${req.method()} ${req.url()}`);
});

// 监听所有响应
page.on('response', async res => {
  console.log(`⬅️ 响应: ${res.status()} ${res.url()}`);
});

// 获取响应 body
const response = await page.waitForResponse('**/api/data');
console.log('响应内容:', await response.text());
```

常用方法：

- request.url() / request.method() / request.headers() / request.postData()
- response.status() / response.headers() / response.text() / response.json()


### 模拟网络环境


## 实例


## 网络拦截相关 API


## 复习重点

- 能说明 `Playwright 网络拦截` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
