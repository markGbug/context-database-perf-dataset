# Playwright：Playwright 视觉回归测试

- 来源：[Playwright 视觉回归测试](https://www.runoob.com/playwright/playwright-visual.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0534

## 本章内容

本章介绍 Playwright 的视觉回归测试功能，通过截图对比检测 UI 的意外变化。


## 什么是视觉回归测试

视觉回归测试（Visual Regression Testing）通过比较当前截图与基准截图（Golden File）之间的像素差异，检测页面的 UI 变化。

当某个 CSS 改动意外影响了其他页面的布局时，视觉回归测试能直接捕获这个问题。


## expect(page).toHaveScreenshot() 页面截图对比


## 实例

第一次运行时，Playwright 会报错并生成基准截图：

```text
Error: A snapshot doesn't exist at runoob-homepage-chromium-darwin.png,
writing actual.
```

第二次运行时，会自动与基准截图对比。


### 完整的 toHaveScreenshot 选项


## 实例


## expect(locator).toHaveScreenshot() 元素截图对比


## 实例


## Golden File 管理


### 生成 Golden File

首次运行截图断言时，Playwright 会自动生成 Golden File 并保存在测试文件旁边的 -snapshots 目录中：

```text
tests/
├── example.spec.ts
└── example.spec.ts-snapshots/
    └── runoob-homepage-chromium-darwin.png
```

文件名包含浏览器名称和操作系统，确保不同平台的基准独立管理。


### 更新 Golden File

当 UI 发生预期的设计变更时，需要更新基准截图：

```text
# 更新所有截图基准
npx playwright test --update-snapshots

# 只更新特定文件
npx playwright test tests/example.spec.ts --update-snapshots
```


## 视觉对比选项详解


## CI 环境注意事项

浏览器渲染结果受操作系统、浏览器版本、硬件、电源状态、headless 模式等因素影响。为确保一致性，请在相同的环境中生成 Golden File 和运行测试。推荐使用 Docker 容器或 CI 的同一平台来消除差异。


### Docker 中使用视觉测试

```text
# 使用 Playwright Docker 镜像确保渲染一致性
docker run --rm -v $(pwd):/work -w /work \
  mcr.microsoft.com/playwright:v1.52.0-jammy \
  npx playwright test --update-snapshots
```


## 视觉测试的最佳实践

- 在相同平台上生成 Golden File 和运行对比
- 使用 animations: 'disabled' 消除动画不确定性
- 使用 mask 忽略动态内容（如时间戳、广告位）
- 优先对关键页面（首页、登录、支付）做视觉回归
- 将 Golden File 提交到版本控制系统
- 在 CI 中使用固定版本的浏览器和操作系统


## 复习重点

- 能说明 `Playwright 视觉回归测试` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
