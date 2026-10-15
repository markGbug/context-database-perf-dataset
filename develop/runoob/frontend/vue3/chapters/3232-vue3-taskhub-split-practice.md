# Vue3：组件拆分

- 来源：[组件拆分](https://www.runoob.com/vue3/vue3-taskhub-split.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3232

## 本章内容

现在的 App.vue 功能已经完备，但所有代码都塞在一起了。

下一步我们将进行组件拆分，你会学到：

- 如何在 Tailwind v4 环境下编写高度复用的 子组件。
- 如何使用 defineProps 和 defineEmits 在 JS 组件间传递数据。

现在在 src/components 目录下新建以下四个文件：

- TaskHeader.vue（纯展示）
- TaskInput.vue（输入逻辑）
- TaskFilter.vue（状态切换）
- TaskItem.vue（单条任务）


### TaskHeader.vue —— 静态展示组件

这个组件不需要任何 JS 逻辑，只需展示 UI。

在 Tailwind v4 中，我们继续使用新的渐变语法。


## 实例


### TaskInput.vue —— 使用 defineEmits 发送数据

这个组件负责获取用户输入。当用户点击添加时，它不直接修改数据，而是通过 emit 通知父组件。


## 实例


### TaskFilter.vue —— 组件间的 v-model 通信

在 Vue 3.4+ 中，推荐使用 defineModel() 来实现双向绑定。这在 Tailwind v4 的 UI 切换中非常高效。


## 实例


### TaskItem.vue —— 使用 defineProps 接收数据

它是最核心的子组件，负责展示单条任务并反馈修改/删除操作。


## 实例


### 重构后的 App.vue (逻辑中枢)

现在的 App.vue 变成了一个干净的指挥官，只负责管理原始数据和处理子组件传来的指令。


## 实例


### 核心知识点总结

defineProps (父传子)：

- TaskItem 通过 props 接收任务数据。在 Vue 中，Props 是只读的。子组件绝不应该直接修改 props 的值，这就是"单向数据流"。

defineEmits (子传父)：

- 当子组件需要改变数据时（如删除、勾选），它通过 emit 发出信号，由父组件执行真正的修改逻辑。这样保证了数据的修改源头只有一个，方便调试。

defineModel (双向绑定神器)：

- 在 TaskFilter 中，我们使用了 Vue 3.4 引入的 defineModel。它极大地简化了父子组件之间状态同步的代码，不再需要手动写 props 和监听 @update:modelValue。

Tailwind v4 的复用性：

- 即使拆分了组件，Tailwind 的原子化类名依然生效。因为 Vite 插件会自动扫描 src 下所有的 .vue 文件并生成对应的样式。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `组件拆分` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
