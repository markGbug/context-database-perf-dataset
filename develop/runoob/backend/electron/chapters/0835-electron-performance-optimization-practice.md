# Electron：Electron 性能优化

- 来源：[Electron 性能优化](https://www.runoob.com/electron/electron-performance-optimization.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0835

## 本章内容

Electron 应用功能强大，但同时可能存在启动慢、内存占用高、包体积大等性能问题。

通过合理优化，可以显著提升用户体验和应用效率。


## 启动性能优化


### 延迟加载

- 将非必要模块或组件延迟加载，避免启动时一次性加载过多内容。
- 示例：在用户第一次操作时才加载特定功能模块。

```javascript
document.getElementById('loadFeature').addEventListener('click', async () => {
  const module = await import('./featureModule.js')
  module.initFeature()
})
```


### 代码分割

- 将主进程与渲染进程逻辑拆分，或者使用 ES 模块动态加载。
- 有助于减少首次加载文件大小。


### 减少启动时的操作

- 避免在 app.whenReady() 中执行复杂计算或网络请求
- 将初始化操作异步化或在后台进程中处理


## 运行时性能优化


### 内存管理

- 避免渲染进程加载大量 DOM 元素或未释放对象
- 使用 Chrome DevTools 监控内存泄漏
- 主进程对象也应及时释放引用

```javascript
// 清理定时器
const interval = setInterval(() => { /* ... */ }, 1000)
clearInterval(interval)
```


### 渲染优化

- 使用虚拟列表或懒加载减少渲染压力
- 避免频繁操作 DOM，尽量批量更新


### 避免内存泄漏

- 避免在渲染进程全局绑定大量事件
- 关闭窗口时解除事件绑定、释放引用

```text
window.onbeforeunload = () => {
  someElement.removeEventListener('click', handler)
}
```


## 打包体积优化


### 依赖分析

- 使用工具分析打包体积，找到大模块或未使用依赖
- 示例工具：webpack-bundle-analyzer


### 移除不必要的依赖

- 检查 package.json 中未使用的模块
- 优化第三方库，避免引入整个库只为一个函数


### 使用 asar 打包

- Electron 提供 .asar 格式打包资源，提高加载速度并减少文件散乱
- 命令示例：electron-packager . myApp --asar


## 多进程优化


### Web Workers 使用

- 对 CPU 密集型任务使用 Web Worker，避免阻塞渲染进程

```javascript
const worker = new Worker('./worker.js')
worker.postMessage({ data: largeData })
worker.onmessage = (e) => console.log('Worker 处理结果', e.data)
```


### 后台任务处理

- 将耗时操作放入主进程或后台进程，通过 IPC 通信返回结果
- 避免渲染进程直接执行复杂逻辑


### 进程池管理

- 对频繁启动的子进程可使用进程池复用，降低系统资源消耗
- 适合图像处理、视频转码等高耗 CPU 的操作


## 小结

Electron 性能优化核心思想：

- 启动快：延迟加载、代码分割、减少启动操作
- 运行顺畅：内存管理、渲染优化、避免泄漏
- 体积小：依赖分析、移除冗余、asar 打包
- 多任务高效：Web Workers、后台处理、进程池管理

通过以上优化手段，Electron 应用可以在桌面端运行得更轻快、稳定和高效。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 性能优化` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
