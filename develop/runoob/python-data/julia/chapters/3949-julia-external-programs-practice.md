# Julia：Julia 运行外部程序

- 来源：[Julia 运行外部程序](https://www.runoob.com/julia/julia-external-programs.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：练习笔记
- 章节序号：3949

## 本章内容

Julia 借鉴 Shell、Perl 和 Ruby 的反引号（backtick）语法来运行外部命令。命令用反引号 `...` 包围：


## 实例

注意：与 Shell 不同，反引号本身不会立即执行命令，而是创建一个 Cmd 对象。Julia 运行命令时不经过 Shell，而是直接 fork/exec 子进程，因此没有通配符展开、管道符等 Shell 特性，也不会有引号转义问题。


## 运行命令：run

run() 函数执行命令，输出直接打印到终端；命令失败会抛出 ProcessFailedException：


## 实例


### 捕获命令输出

用 read() 可以捕获命令的输出，readchomp() 还会去掉结尾的换行：


## 实例


### 插值

反引号命令同样支持 $ 插值，Julia 会自动处理好参数引号和转义，不用担心特殊字符问题：


## 实例


## 管道：pipeline

Shell 的 |、&、> 在反引号里需要转义，构造管道要用 pipeline() 函数：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Julia 运行外部程序` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
