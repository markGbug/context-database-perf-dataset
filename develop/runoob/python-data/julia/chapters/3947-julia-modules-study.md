# Julia：Julia 模块与包管理

- 来源：[Julia 模块与包管理](https://www.runoob.com/julia/julia-modules.html)
- 分类：Python / 数据科学
- 技术：Julia
- 笔记类型：学习笔记
- 章节序号：3947

## 本章内容

模块（module）用于把代码组织成独立的命名空间，避免命名冲突；包（package）则是打包发布的模块，通过内置的包管理器 Pkg 安装。


## 定义模块

使用 module ... end 定义模块：


## 实例


### 访问模块成员的三种方式


## 实例

using 与 import 的区别总结：

注意：上面的例子中 using .MyModule 里的点表示"当前作用域中定义的模块"。从 REPL 或脚本中加载本地模块必须加点前缀；从已安装的包加载则直接写包名，如 using Example。


### include 与多文件模块

实际项目中，模块代码通常拆分到多个文件，用 include() 组装：


## 实例


### 标准模块


## 包管理器 Pkg

Julia 自带包管理器 Pkg，可以在 REPL 的 Pkg 模式中使用（输入 ] 进入），也可以通过 using Pkg 在代码中调用。


### Pkg 模式常用命令


## 实例：安装并使用第三方包

代码中等价的写法：


## 实例


### 使用标准库

标准库随 Julia 一起安装，直接 using 即可，不需要 add：


## 实例


## 环境（Environment）

Julia 的包安装在环境中。每个环境由一个项目目录描述，包含两个文件：


### 创建并使用项目环境


## 实例

最佳实践：不要把所有包装进默认环境（@v1.10），而是为每个项目建独立环境。这样不同项目可以使用同一个包的不同版本，互不干扰，还能通过提交 Project.toml 让别人精确复现你的环境。


## 开发自己的包

用 Pkg 可以快速生成一个包的骨架：

```text
julia> ] generate MyPkg
Generating  project MyPkg:
    MyPkg/Project.toml
    MyPkg/src/MyPkg.jl
```

生成的包主文件结构如下：


## MyPkg/src/MyPkg.jl 文件

在包目录下启动 Julia 并激活环境后，就可以直接 using 自己的包：

```text
julia> ] activate MyPkg
julia> using MyPkg

julia> greet()
"Hello from MyPkg!"
```


### 扩展 Base 函数时的 import 写法

在自己包里给 Base 的函数添加新方法时，建议用 import 明确声明：


## 实例


## 复习重点

- 能说明 `Julia 模块与包管理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
