# Kotlin：Kotlin 教程

- 来源：[Kotlin 教程](https://www.runoob.com/kotlin/kotlin-tutorial.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3363

## 本章内容

Kotlin 是一门运行在 Java 虚拟机上的静态类型编程语言，由 JetBrains 开发。

Kotlin 语法简洁、天生支持空安全，并且可以和 Java 代码互相调用，是 Android 开发的官方首选语言。

Kotlin 可以编译成 Java 字节码，也可以编译成 JavaScript，方便在没有 JVM 的设备上运行。

本教程基于 Kotlin 2.2 编写，从零开始带你掌握 Kotlin 的语法、面向对象、集合、协程与工程实践。


## 我的第一个 Kotlin 程序

Kotlin 程序文件以 .kt 结尾，如：hello.kt 、app.kt。


## 最简版

```html
package hello                      //  可选的包头

fun main(args: Array<String>) {    // 包级可见的函数，接受一个字符串数组作为参数
   println("Hello World!")         // 分号可以省略
}
```


## 面向对象

```html
class Greeter(val name: String) {
   fun greet() {
      println("Hello, $name")
   }
}

fun main(args: Array<String>) {
   Greeter("World!").greet()          // 创建一个对象不用 new 关键字
}
```


## 为什么选择 Kotlin？

- 简洁: 大大减少样板代码的数量。
- 安全: 避免空指针异常等整个类的错误。
- 互操作性: 充分利用 JVM、Android 和浏览器的现有库。
- 工具友好: 可用任何 Java IDE 或者使用命令行构建。


## 参考链接

- 官方网站
- 官方示例
- Kotlin 官方在线工具
- Kotlin 在线工具


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
