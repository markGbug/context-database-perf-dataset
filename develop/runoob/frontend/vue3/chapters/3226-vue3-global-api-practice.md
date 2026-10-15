# Vue3：Vue3 全局 API

- 来源：[Vue3 全局 API](https://www.runoob.com/vue3/vue3-global-api.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3226

## 本章内容

Vue3 全局 API 如下：


## 应用实例 API


### 1. createApp()

- 功能: 创建一个 Vue 应用实例。
- 用法: createApp(rootComponent, rootProps)
- 参数: rootComponent: 根组件。 rootProps (可选): 传递给根组件的 props。


## 实例


### 2. createSSRApp()

- 功能: 创建一个支持服务器端渲染 (SSR) 的 Vue 应用实例。
- 用法: createSSRApp(rootComponent, rootProps)
- 参数: rootComponent: 根组件。 rootProps (可选): 传递给根组件的 props。


## 实例


### 3. app.mount()

- 功能: 将应用挂载到 DOM 元素上。
- 用法: app.mount(container)
- 参数: container: DOM 元素或选择器字符串。


## 实例


### 4. app.unmount()

- 功能: 卸载应用实例。
- 用法: app.unmount()


## 实例


### 5. app.onUnmount()

- 功能: 注册一个回调函数，在应用卸载时调用。
- 用法: app.onUnmount(callback)
- 参数: callback: 卸载时调用的函数。


## 实例


### 6. app.component()

- 功能: 注册或获取全局组件。
- 用法: 注册: app.component(name, component) 获取: app.component(name)
- 参数: name: 组件名称。 component: 组件定义。


## 实例


### 7. app.directive()

- 功能: 注册或获取全局指令。
- 用法: 注册: app.directive(name, directive) 获取: app.directive(name)
- 参数: name: 指令名称。 directive: 指令定义。


## 实例


### 8. app.use()

- 功能: 安装插件。
- 用法: app.use(plugin, options)
- 参数: plugin: 插件。 options (可选): 插件选项。


## 实例


### 9. app.mixin()

- 功能: 全局混入选项。
- 用法: app.mixin(mixin)
- 参数: mixin: 混入对象。


## 实例


### 10. app.provide()

- 功能: 提供全局依赖。
- 用法: app.provide(key, value)
- 参数: key: 依赖名称。 value: 依赖值。


## 实例


### 11. app.runWithContext()

- 功能: 在当前应用上下文中运行函数。
- 用法: app.runWithContext(fn)
- 参数: fn: 要运行的函数。


## 实例


### 12. app.version

- 功能: 获取 Vue 版本。
- 用法: app.version


## 后续章节

- 实例
- 13. app.config
- 实例
- 14. app.config.errorHandler
- 实例
- 15. app.config.warnHandler
- 实例
- 16. app.config.performance
- 实例
- 17. app.config.compilerOptions
- 实例
- 18. app.config.globalProperties
- 实例
- 19. app.config.optionMergeStrategies
- 实例
- 20. app.config.idPrefix

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 全局 API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
