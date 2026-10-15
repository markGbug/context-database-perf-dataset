# 知识点 37405：C：C 标准库 - <time.h> - 库变量

- 来源：[C 标准库 - <time.h>](https://www.runoob.com/cprogramming/c-standard-library-time-h.html)
- 来源章节：[3530-c-standard-library-time-h-practice.md](../chapters/3530-c-standard-library-time-h-practice.md)
- 分类：编程语言
- 技术：C
- 所在小节：库变量
- 知识类型：代码
- 原章节序号：3530

## 原文片段

```text
struct tm {
   int tm_sec;         /* 秒，范围从 0 到 59        */
   int tm_min;         /* 分，范围从 0 到 59        */
   int tm_hour;        /* 小时，范围从 0 到 23        */
   int tm_mday;        /* 一月中的第几天，范围从 1 到 31    */
   int tm_mon;         /* 月，范围从 0 到 11        */
   int tm_year;        /* 自 1900 年起的年数        */
   int tm_wday;        /* 一周中的第几天，范围从 0 到 6    */
   int tm_yday;        /* 一年中的第几天，范围从 0 到 365    */
   int tm_isdst;       /* 夏令时                */
};
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `库变量` 这一小节和 `C 标准库 - <time.h>` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
