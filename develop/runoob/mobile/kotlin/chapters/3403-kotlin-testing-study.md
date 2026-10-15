# Kotlin：Kotlin 测试

- 来源：[Kotlin 测试](https://www.runoob.com/kotlin/kotlin-testing.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3403

## 本章内容

测试是保证代码正确性的第一道防线，它让你在修改代码后能快速确认没有破坏已有功能。

Kotlin 提供了跨平台的测试库 kotlin.test，配合 JUnit 就能写出简洁、可读的单元测试。


## kotlin.test 与 JUnit

这两个名字经常一起出现，但它们的职责并不相同。

JUnit 是 JVM 上最主流的测试框架，负责发现测试方法、组织执行流程、生成测试报告。

kotlin.test 是 Kotlin 官方提供的测试库，它定义了一套统一的断言 API 和注解。

kotlin.test 本身不是框架，它通过适配器把断言转发给底层的测试框架，在 JVM 上默认就是 JUnit。

这样写出来的测试代码可以跨平台复用，在 Kotlin/JS、Kotlin/Native 上换一个适配器即可。

提示：JUnit 4 与 JUnit 5 的包名和注解都不同。新项目直接使用 JUnit 5，它的扩展模型更灵活，Gradle 也需要显式声明 useJUnitPlatform()。


## 引入依赖

在 Gradle 项目中，测试依赖写在 testImplementation 配置里，只在测试源码集可见。

kotlin("test") 会自动选择与当前测试框架匹配的适配器版本。


## 实例

测试源码放在 src/test/kotlin 目录下，包名与主代码保持一致。

下面是被测的业务代码，文件路径 src/main/kotlin/com/runoob/Calculator.kt。


## 实例


## 第一个测试

测试类通常与被测类同名并加上 Test 后缀，测试方法用 @Test 注解标记。

方法名建议直接描述被测行为，让失败的测试报告一眼就能看懂。


## 实例

执行 gradlew test 后，三个测试全部通过。

```text
$ ./gradlew test

> Task :test
BUILD SUCCESSFUL in 2s

3 tests completed
```

如果断言失败，报告里会给出期望值与实际值的对比，定位问题非常直接。

```text
$ ./gradlew test

> Task :test FAILED

CalculatorTest > addReturnsSumOfTwoNumbers FAILED
    java.lang.AssertionError at CalculatorTest.kt:16
        expected: 6 but was: 5

BUILD FAILED in 2s
```


## 断言函数表

kotlin.test 提供了一组命名清晰的断言函数，覆盖了绝大多数测试场景。

断言失败时抛出 AssertionError，Gradle 会把失败信息汇总到测试报告中。

assertEquals 还有一个带消息参数的重载，在断言失败时输出自定义提示。


## 实例


## 测试生命周期

多个测试方法常常需要共享同一套初始化与清理逻辑，例如建立数据库连接、创建临时文件。

kotlin.test 提供了四个生命周期注解，它们在每个测试方法前后各执行一次。

@BeforeAll 与 @AfterAll 来自 JUnit 5，在 Kotlin 中需要写在伴生对象里并加上 @JvmStatic，否则框架找不到它们。


## 实例

在 JVM 上，kotlin.test 的注解会映射到 JUnit 5 的对应注解，@BeforeTest 等价于 @BeforeEach，@AfterTest 等价于 @AfterEach。

注意：不要在 @BeforeTest 里做特别耗时的操作，因为它会被每个测试方法执行一次。如果确实需要，改用 @BeforeClass 只执行一次。


## 参数化测试

同一段逻辑需要用多组数据验证时，复制多个测试方法既啰嗦又难维护。

参数化测试把数据抽成表格，框架会自动为每一行数据生成一个独立的测试用例。

kotlin.test 本身不提供参数化注解，在 JVM 上使用 JUnit 5 的 @ParameterizedTest 即可。


## 实例

运行后报告中会显示四个独立的用例，任何一个失败都能立刻看出是哪组数据出了问题。

```text
$ ./gradlew test

> Task :test
CalculatorParameterizedTest > 1 + 2 = 3 PASSED
CalculatorParameterizedTest > 0 + 0 = 0 PASSED
CalculatorParameterizedTest > -1 + 1 = 0 PASSED
CalculatorParameterizedTest > 100 + 200 = 300 PASSED

BUILD SUCCESSFUL in 2s
```


## 协程测试

挂起函数不能直接在普通测试方法里调用，需要用 runTest 包起来。

runTest 来自 kotlinx-coroutines-test，它会创建一个虚拟时间的测试调度器。

代码里的 delay 会被立即跳过，测试不需要真的等待一秒，跑起来非常快。


## 实例


## 实例

如果被测代码内部启动了协程，runTest 会在测试结束前等待它们完成，避免出现「测试通过了但协程还在跑」的假象。

提示：runTest 返回的是 TestScope，可以用 testScheduler.advanceTimeBy(1000) 手动推进虚拟时间，验证超时或延迟逻辑。


## Gradle 运行测试

Gradle 的 test 任务会编译并执行所有测试，同时生成 HTML 报告。

开发时经常只需要跑某一个测试类或某一个方法，用 --tests 参数即可过滤。

测试报告默认生成在 build/reports/tests/test/index.html，用浏览器打开即可查看每个用例的结果与耗时。

```text
$ ./gradlew test --tests "com.runoob.CalculatorTest"

> Task :test
BUILD SUCCESSFUL in 1s

3 tests completed, 3 passed
```

持续集成环境里通常会在测试命令后加上 --no-daemon，避免守护进程占用内存。


## 常见问题

下面这些是初写测试时最容易踩的坑。


### 测试找不到 @Test 注解

确认导包是 kotlin.test.Test 还是 org.junit.jupiter.api.Test，两者不能混用。

同一个测试类里统一使用一种即可，kotlin.test 的注解在 JVM 上会委托给 JUnit 执行。


### useJUnitPlatform 没有配置

JUnit 5 必须显式声明 tasks.test { useJUnitPlatform() }，否则 Gradle 默认用 JUnit 4 的平台，测试根本不会被执行。


### 测试之间有依赖导致结果不稳定

每个测试方法都应该是独立的，不要依赖执行顺序。

把共享状态放在 @BeforeTest 里重建，而不是在类初始化时创建一次。


### 测试速度慢

优先排查是否真的在等待网络或数据库。协程里的 delay 用 runTest 跳过，外部依赖用假实现替换。

只跑受影响的测试类，而不是每次都跑全量。


## 复习重点

- 能说明 `Kotlin 测试` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
