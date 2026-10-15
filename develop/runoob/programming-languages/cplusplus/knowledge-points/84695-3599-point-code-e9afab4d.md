# 知识点 84695：C++：C++ <unordered_map> - 构造函数

- 来源：[C++ <unordered_map>](https://www.runoob.com/cplusplus/cpp-libs-unordered_map.html)
- 来源章节：[3599-cpp-libs-unordered_map-practice.md](../chapters/3599-cpp-libs-unordered_map-practice.md)
- 分类：编程语言
- 技术：C++
- 所在小节：构造函数
- 知识类型：代码
- 原章节序号：3599

## 原文片段

```text
// 默认构造
std::unordered_map<int, std::string> myMap;

// 构造并初始化
std::unordered_map<int, std::string> myMap = {{1, "one"}, {2, "two"}};

// 构造并指定初始容量
std::unordered_map<int, std::string> myMap(10);

// 构造并复制另一个 unordered_map
std::unordered_map<int, std::string> anotherMap = myMap;
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `构造函数` 这一小节和 `C++ <unordered_map>` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
