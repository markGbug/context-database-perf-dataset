# Go：Go 错误处理

- 来源：[Go 错误处理](https://www.runoob.com/go/go-error-handling.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：练习笔记
- 章节序号：0868

## 本章内容

Go 语言通过内置的错误接口提供了非常简单的错误处理机制。

Go 语言的错误处理采用显式返回错误的方式，而非传统的异常处理机制。这种设计使代码逻辑更清晰，便于开发者在编译时或运行时明确处理错误。

Go 的错误处理主要围绕以下机制展开：

- error 接口：标准的错误表示。
- 显式返回值：通过函数的返回值返回错误。
- 自定义错误：可以通过标准库或自定义的方式创建错误。
- panic 和 recover：处理不可恢复的严重错误。


## error 接口

Go 标准库定义了一个 error 接口，表示一个错误的抽象。

error 类型是一个接口类型，这是它的定义：

```text
type error interface {
    Error() string
}
```

- 实现 error 接口：任何实现了 Error() 方法的类型都可以作为错误。
- Error() 方法返回一个描述错误的字符串。


### 使用 errors 包创建错误

我们可以在编码中通过实现 error 接口类型来生成错误信息。

创建一个简单错误：


## 实例

函数通常在最后的返回值中返回错误信息，使用 errors.New 可返回一个错误信息：

```text
func Sqrt(f float64) (float64, error) {
    if f < 0 {
        return 0, errors.New("math: square root of negative number")
    }
    // 实现
}
```

在下面的例子中，我们在调用 Sqrt 的时候传递的一个负数，然后就得到了 non-nil 的 error 对象，将此对象与 nil 比较，结果为 true，所以 fmt.Println(fmt 包在处理 error 时会调用 Error 方法)被调用，以输出错误，请看下面调用的示例代码：

```text
result, err:= Sqrt(-1)

if err != nil {
   fmt.Println(err)
}
```


## 显式返回错误

Go 中，错误通常作为函数的返回值返回，开发者需要显式检查并处理。

显式返回错误：


## 实例

输出：

```text
Error: division by zero
```


## 自定义错误

通过定义自定义类型，可以扩展 error 接口。

自定义错误类型：


## 实例


## fmt 包与错误格式化

fmt 包提供了对错误的格式化输出支持：

- %v：默认格式。
- %+v：如果支持，显示详细的错误信息。
- %s：作为字符串输出。


## 实例

执行以上程序，输出结果为：

```text
100/10 =  10
errorMsg is:
    Cannot proceed, the divider is zero.
    dividee: 100
    divider: 0
```


## 使用 errors.Is 和 errors.As

从 Go 1.13 开始，errors 包引入了 errors.Is 和 errors.As 用于处理错误链：


### errors.Is

检查某个错误是否是特定错误或由该错误包装而成。


## 实例


### errors.As

将错误转换为特定类型以便进一步处理。


## 实例


## panic 和 recover

Go 的 panic 用于处理不可恢复的错误，recover 用于从 panic 中恢复。

panic:

- 导致程序崩溃并输出堆栈信息。
- 常用于程序无法继续运行的情况。

recover:

- 捕获 panic，避免程序崩溃。


## 实例

执行以上代码，输出结果为：

```text
Starting program...
Recovered from panic: something went wrong
Program continued after panic
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Go 错误处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
