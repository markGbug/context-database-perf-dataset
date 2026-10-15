# React：React 组件 API

- 来源：[React 组件 API](https://www.runoob.com/react/react-component-api.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3049

## 本章内容

React 组件 API 涉及多个重要的方面，包括生命周期方法、状态管理、属性传递和事件处理。

以下是 React 组件 API 的详细说明：


## 生命周期方法

React 组件的生命周期方法分为三个主要阶段：挂载、更新和卸载，详细说明参见：React 组件的生命周期 。


### 挂载阶段

- constructor(props): 构造函数，用于初始化状态或绑定方法。
- static getDerivedStateFromProps(props, state): 每次在调用 render 方法之前调用，用于更新状态。
- componentDidMount(): 组件挂载后调用，此时可以进行 DOM 操作或数据请求。


## 实例


### 更新阶段

- static getDerivedStateFromProps(props, state): 与挂载阶段相同，用于更新状态。
- shouldComponentUpdate(nextProps, nextState): 返回布尔值，决定组件是否重新渲染。
- render(): 渲染组件的 UI。
- getSnapshotBeforeUpdate(prevProps, prevState): 在 DOM 更新之前调用，用于捕获一些信息（如滚动位置）。
- componentDidUpdate(prevProps, prevState, snapshot): 在组件更新后调用。


## 实例


### 卸载阶段

- componentWillUnmount(): 组件即将卸载时调用，用于清理资源（如定时器、事件监听等）。


## 实例


## 状态管理

状态是一个组件内部的数据，使用 this.state 来定义和管理。通过 setState 方法更新状态。


## 实例


## 属性传递

通过 this.props 访问传递给组件的属性，可以使用 PropTypes 进行类型检查。


## 实例


## 事件处理

通过事件处理函数处理用户交互。需要使用 .bind(this) 或箭头函数来确保 this 指向正确。


## 实例


## 条件渲染

通过条件语句控制组件的渲染。


## 实例


## 列表渲染

通过数组的 map 方法渲染列表。


## 实例


## 受控组件

通过状态控制表单元素的值。


## 实例


## 设置状态:setState

setState 是 React 中用于更新组件状态的方法。

语法格式如下：

```javascript
setState(object nextState[, function callback])
```


### 参数说明

- object nextState: 一个对象，包含要更新的状态键值对。React 会将这个对象合并到当前状态中。
- function callback: 一个可选的回调函数，会在状态更新并重新渲染完成后执行。

合并 nextState 和当前 state，并重新渲染组件。

setState 是 React 事件处理函数中和请求回调函数中触发 UI 更新的主要方法。


### 关于setState

不能在组件内部通过 this.state 修改状态，因为该状态会在调用 setState() 后被替换。

setState() 并不会立即改变 this.state，而是创建一个即将处理的 state。setState() 并不一定是同步的，为了提升性能 React 会批量执行 state 和 DOM 渲染。

setState()总是会触发一次组件重绘，除非在 shouldComponentUpdate() 中实现了一些条件渲染逻辑。

通过合理使用 setState，可以有效地管理组件状态，并确保在状态更新后执行必要的操作，从而提高应用的响应性和可靠性。


## React 实例

```html
class Counter extends React.Component{
  constructor(props) {
      super(props);
      this.state = {clickCount: 0};
      this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(function(state) {
      return {clickCount: state.clickCount + 1};
    });
  }
  render () {
    return (<h2 onClick={this.handleClick}>点我！点击次数为: {this.state.clickCount}</h2>);
  }
}
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <Counter />
);
```

实例中通过点击 h2 标签来使得点击计数器加 1。


## 复习重点

- 能说明 `React 组件 API` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
