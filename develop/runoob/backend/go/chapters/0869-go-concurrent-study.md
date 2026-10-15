# Go：Go 并发

- 来源：[Go 并发](https://www.runoob.com/go/go-concurrent.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：学习笔记
- 章节序号：0869

## 本章内容

并发是指程序同时执行多个任务的能力。

Go 语言支持并发，通过 goroutines 和 channels 提供了一种简洁且高效的方式来实现并发。

Goroutines：

- Go 中的并发执行单位，类似于轻量级的线程。
- Goroutine 的调度由 Go 运行时管理，用户无需手动分配线程。
- 使用 go 关键字启动 Goroutine。
- Goroutine 是非阻塞的，可以高效地运行成千上万个 Goroutine。

Channel：

- Go 中用于在 Goroutine 之间通信的机制。
- 支持同步和数据共享，避免了显式的锁机制。
- 使用 chan 关键字创建，通过 <- 操作符发送和接收数据。

Scheduler（调度器）：

Go 的调度器基于 GMP 模型，调度器会将 Goroutine 分配到系统线程中执行，并通过 M 和 P 的配合高效管理并发。

- G：Goroutine。
- M：系统线程（Machine）。
- P：逻辑处理器（Processor）。


## Goroutine

goroutine 是轻量级线程，goroutine 的调度是由 Golang 运行时进行管理的。

goroutine 语法格式：

```text
go 函数名( 参数列表 )
```

例如：

```text
go f(x, y, z)
```

开启一个新的 goroutine:

```text
f(x, y, z)
```

Go 允许使用 go 语句开启一个新的运行期线程， 即 goroutine，以一个不同的、新创建的 goroutine 来执行一个函数。 同一个程序中的所有 goroutine 共享同一个地址空间。


## 实例

执行以上代码，你会看到输出的 Main 和 Hello。输出是没有固定先后顺序，因为它们是两个 goroutine 在执行：

```text
Main
Hello
Main
Hello
...
```


## 通道（Channel）

通道（Channel）是用于 Goroutine 之间的数据传递。

通道可用于两个 goroutine 之间通过传递一个指定类型的值来同步运行和通讯。

使用 make 函数创建一个 channel，使用 <- 操作符发送和接收数据。如果未指定方向，则为双向通道。

```text
ch <- v    // 把 v 发送到通道 ch
v := <-ch  // 从 ch 接收数据
           // 并把值赋给 v
```

声明一个通道很简单，我们使用chan关键字即可，通道在使用前必须先创建：

```text
ch := make(chan int)
```

注意：默认情况下，通道是不带缓冲区的。发送端发送数据，同时必须有接收端相应的接收数据。

以下实例通过两个 goroutine 来计算数字之和，在 goroutine 完成计算后，它会计算两个结果的和：


## 实例

输出结果为：

```text
-5 17 12
```


### 通道缓冲区

通道可以设置缓冲区，通过 make 的第二个参数指定缓冲区大小：

```text
ch := make(chan int, 100)
```

带缓冲区的通道允许发送端的数据发送和接收端的数据获取处于异步状态，就是说发送端发送的数据可以放在缓冲区里面，可以等待接收端去获取数据，而不是立刻需要接收端去获取数据。

不过由于缓冲区的大小是有限的，所以还是必须有接收端来接收数据的，否则缓冲区一满，数据发送端就无法再发送数据了。

注意：如果通道不带缓冲，发送方会阻塞直到接收方从通道中接收了值。如果通道带缓冲，发送方则会阻塞直到发送的值被拷贝到缓冲区内；如果缓冲区已满，则意味着需要等待直到某个接收方获取到一个值。接收方在有值可以接收之前会一直阻塞。


## 实例

执行输出结果为：

```text
1
2
```


### Go 遍历通道与关闭通道

Go 通过 range 关键字来实现遍历读取到的数据，类似于与数组或切片。格式如下：

```text
v, ok := <-ch
```

如果通道接收不到数据后 ok 就为 false，这时通道就可以使用 close() 函数来关闭。


## 实例

执行输出结果为：

```text
0
1
1
2
3
5
8
13
21
34
```


### Select 语句

select 语句使得一个 goroutine 可以等待多个通信操作。select 会阻塞，直到其中的某个 case 可以继续执行：


## 实例

以上代码中，fibonacci goroutine 在 channel c 上发送斐波那契数列，当接收到 quit channel 的信号时退出。

执行输出结果为：

```text
0
1
1
2
3
5
8
13
21
34
quit
```


## 使用 WaitGroup

sync.WaitGroup 用于等待多个 Goroutine 完成。

同步多个 Goroutine：


## 实例

以上代码，执行输出结果如下：

```text
Worker 1 started
Worker 1 finished
Worker 2 started
Worker 2 finished
Worker 3 started
Worker 3 finished
All workers done
```


## 高级特性

Buffered Channel：

创建有缓冲的 Channel。

```text
ch := make(chan int, 2)
```

Context：

用于控制 Goroutine 的生命周期。

```text
context.WithCancel、context.WithTimeout。
```

Mutex 和 RWMutex：

sync.Mutex 提供互斥锁，用于保护共享资源。

```javascript
var mu sync.Mutex
mu.Lock()
// critical section
mu.Unlock()
```


## 并发编程小结

Go 语言通过 Goroutine 和 Channel 提供了强大的并发支持，简化了传统线程模型的复杂性。配合调度器和同步工具，可以轻松实现高性能并发程序。

- Goroutines 是轻量级线程，使用 go 关键字启动。
- Channels 用于 goroutines 之间的通信。
- Select 语句 用于等待多个 channel 操作。


### 常见问题

死锁 (Deadlock)：

- 示例：所有 Goroutine 都在等待，但没有任何数据可用。
- 解决：避免无限等待、正确关闭通道。

数据竞争 (Data Race)：

- 示例：多个 Goroutine 同时访问同一变量。
- 解决：使用 Mutex 或 Channel 同步访问。


## 复习重点

- 能说明 `Go 并发` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
