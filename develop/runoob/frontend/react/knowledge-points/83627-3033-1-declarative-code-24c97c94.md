# 知识点 83627：React：React 简介 - 1. 声明式编程（Declarative）

- 来源：[React 简介](https://www.runoob.com/react/react-intro.html)
- 来源章节：[3033-react-intro-practice.md](../chapters/3033-react-intro-practice.md)
- 分类：前端开发
- 技术：React
- 所在小节：1. 声明式编程（Declarative）
- 知识类型：代码
- 原章节序号：3033

## 原文片段

```text
// React（声明式）
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `1. 声明式编程（Declarative）` 这一小节和 `React 简介` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
