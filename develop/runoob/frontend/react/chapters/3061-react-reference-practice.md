# React：React 参考手册

- 来源：[React 参考手册](https://www.runoob.com/react/react-reference.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3061

## 本章内容

React 手册包含了各种核心 API、Hooks、组件生命周期方法等。

以下是一份完整的 React 参考手册，内容覆盖从基础到高级的所有核心概念（基于 React 18+ 现代实践，优先函数组件 + Hooks），每个表格包含概念/语法、描述、示例代码 和 注意事项。


### 1、JSX 基础


### 2、 组件基础


### 3、状态与 Hooks（核心）


### 4、生命周期（类组件 vs Hooks）


### 5、上下文与全局状态


### 6、高级特性（React 18+）


### 7、性能优化


### 8、常见生态工具


### 9、调试与最佳实践

以下是一些常见的函数和方法，以及它们的简要说明：


## React 核心 API

createElement(type, [props], [...children]) - 创建一个 React 元素或组件。


## 实例

cloneElement(element, [props], [...children]) - 克隆并返回一个 React 元素，可以传递新的 props 和子元素。


## 实例

createFactory(type) - 创建一个工厂函数，用于创建指定类型的 React 元素。


## 实例

isValidElement(element) - 判断一个对象是否是有效的 React 元素。


## 实例

Children.map(children, function[(thisArg)]) - 遍历和映射 React 子元素。


## 实例


## React 组件生命周期方法

constructor(props) - 构造函数，在组件创建时调用，用于初始化 state 和绑定方法。


## 实例

componentDidMount() - 组件挂载后调用，通常用于数据获取、订阅等副作用操作。


## 实例

componentDidUpdate(prevProps, prevState) - 组件更新后调用，通常用于响应 props 或 state 的变化。


## 实例

componentWillUnmount() - 组件将被卸载前调用，用于清理定时器、取消订阅等资源释放。


## 实例

static getDerivedStateFromProps(props, state) - 用于替代 componentWillReceiveProps，在 props 变化时更新 state。


## 实例


## React Hooks

useState(initialState) - 声明一个状态变量及其更新函数。


## 实例

useEffect(callback, [dependencies]) - 声明一个副作用操作，类似于 componentDidMount 和 componentDidUpdate 的组合。


## 实例

useContext(context) - 获取并订阅一个 React context。


## 后续章节

- 实例
- 实例
- 实例
- 实例
- 实例
- 其他常见函数
- 实例
- 实例
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `React 参考手册` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
