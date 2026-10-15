# DeepSeek Harness：DeepSeek Harness 实战：写一个可替换的能力

- 来源：[DeepSeek Harness 实战](https://www.runoob.com/deepseek-harness/deepseek-harness-build-capability.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：练习笔记
- 章节序号：0235

## 本章内容

上一章节讲了三角色的概念，这一篇我们将按照官方教程把它写成代码。

我们要实现一个叫 myCap 的能力：输入一段文本，输出全部大写，它小到一眼看懂，又完整覆盖 Definition、Provider、Consumer 三个包。

三步走：Service Definition（抽象类 + 类型）→ Service Provider（实现子类）→ Consumer（defineTool）。

最后在 cordis.yml 里把 Provider 与 Consumer 组合加载。


## 第一步：编写 Service Definition

Service Definition 声明能力本身：服务叫什么、怎么调用、请求与结果的类型是什么。

它不包含任何实现逻辑，只有一个抽象方法和两个接口。

抽象类 MyCapService 继承自 Service，通过 super(ctx, 'myCap') 注册为命名服务。

declare module 声明合并让 ctx.myCap 拥有类型，这个技巧在第 14 篇讲过。


## 实例

abstract execute 是唯一的抽象方法，Provider 必须实现它。

MyCapRequest 拥有 input 字段，MyCapResult 拥有 output 字段。

请求与结果类型由 Definition 包拥有，Provider 与 Consumer 都从它导入。


## 第二步：编写 Service Provider

Service Provider 继承抽象类，填上真正的行为。

MyCapLocal 把 input 变成大写后返回。

export const name 声明插件名，apply 里通过 ctx.plugin(MyCapLocal) 注册服务实现。


## 实例

Provider 只依赖 Definition 包里的抽象类和类型。

它不关心模型怎么调用，也不关心工具长什么样。

将来想换一种实现，例如在远程服务器上执行，只需再写一个 Provider 子类。


## 第三步：编写消费方 Consumer

Consumer 把能力包装成模型可以调用的工具。

inject 声明依赖 tools 与 myCap，保证这两个服务就绪后再执行 apply。

defineTool 声明工具 schema，模型看到 my_cap 工具后就会按 parameters 传参。

execute 里调用 ctx.myCap.execute，把结果作为工具输出返回。


## 实例

模型不直接认识 ctx.myCap，它只认识 my_cap 工具。

Consumer 是两者之间的桥梁，也负责把结果渲染成模型可见的文本。


## myCap 三角色结构与数据流

把三个包拼在一起，数据从模型出发，流经 Consumer、Definition，落到 Provider。

模型先调用 my_cap 工具，这一步只发生在 Consumer 层。

Consumer 把参数包装成 MyCapRequest，交给 ctx.myCap.execute(request)。

Definition 把调用委托给当前加载的 Provider 实现。

Provider 算出结果后，沿原路把 MyCapResult 返回给 Consumer。

Consumer 把 output 渲染成文本，作为工具结果交给模型。

整条链路里，Provider 被换掉时，Consumer 与模型都无感知。


## 在 cordis.yml 中组合

三个包写完只是零件，还要在 cordis.yml 里把 Provider 与 Consumer 一起加载。

加载 Provider，ctx.myCap 才有实现；加载 Consumer，模型才有 my_cap 工具。


## 实例

加载顺序上，Cordis 会按依赖自动排序，因此 Provider 与 Consumer 谁先谁后并不关键。

想换成别的 Provider 时，只改第一行，Consumer 保持不变。


## 设计要点

官方文档给了三条设计要点，写能力之前最好先记住。

第一条，不要预防性拆分。

只有角色需要独立演进时，才把它们放进不同的包。

简单的工具插件不需要拆分，一个包承担多个角色完全合法。

第二条，Service Definition 拥有 Request/Result 类型。

Provider 和 Consumer 只依赖 Definition 包，因此请求与结果类型必须由 Definition 定义。

第三条，显式优于隐式。

实现应通过显式的 resolve(request) 步骤处理默认值，而不是在 run() 里隐藏 ?? default。

Bash seam 就是例子：ShellExecRequest 的 workdir、timeoutMs 是可选的，工具层先调用 ctx.shell.resolve(request) 得到全部字段必填的 ShellExecSpec，再交给 run()。

不要在 run() 内部悄悄补默认值；先 resolve，再执行，边界才清晰。


## 小结与自测

一句话总结：写一个可替换能力 = Definition 抽象类 + Provider 子类 + Consumer 工具，再加一份 cordis.yml。

自测题一：MyCapRequest 和 MyCapResult 应该定义在哪个包里？

自测题二：Provider 与 Consumer 之间有没有依赖？

自测题三：为什么简单的工具插件不建议预防性拆分？


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DeepSeek Harness 实战` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
