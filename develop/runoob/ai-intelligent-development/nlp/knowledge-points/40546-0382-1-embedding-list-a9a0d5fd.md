# 知识点 40546：自然语言处理 NLP：BERT 系列模型 - 1. 输入层（Embedding）

- 来源：[BERT 系列模型](https://www.runoob.com/nlp/bert-encoder.html)
- 来源章节：[0382-bert-encoder-study.md](../chapters/0382-bert-encoder-study.md)
- 分类：AI / 智能开发
- 技术：自然语言处理 NLP
- 所在小节：1. 输入层（Embedding）
- 知识类型：要点
- 原章节序号：0382

## 原文片段

Embedding 层：将每个词转换为固定维度的向量表示（如 768 维），包含： 词嵌入（Token Embeddings）：词汇的语义信息。 位置嵌入（Position Embeddings）：词在序列中的位置信息。 段嵌入（Segment Embeddings）：区分句子（对句对任务有用，如图中未显式展示）。

## 学习理解

这是一个列表型要点，通常用于总结特性、规则、组成部分或注意事项。复习时要把它放回本章上下文。

- 它属于哪一类规则或特性？
- 和同组其他要点有什么区别？
- 有没有可以补充的例子或反例？

## 复习问题

- `1. 输入层（Embedding）` 这一小节和 `BERT 系列模型` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
