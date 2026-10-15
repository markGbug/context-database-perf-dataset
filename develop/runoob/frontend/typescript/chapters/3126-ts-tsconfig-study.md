# TypeScript：TypeScript tsconfig.json 配置

- 来源：[TypeScript tsconfig.json](https://www.runoob.com/typescript/ts-tsconfig.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3126

## 本章内容

tsconfig.json 是 TypeScript 项目的配置文件，用于指定编译选项和项目设置。


## 基本配置

最基础的 tsconfig.json 文件。


## 实例

配置说明：

- target：编译目标 JavaScript 版本
- module：使用的模块系统
- strict：启用所有严格类型检查
- outDir：输出目录


## 编译目标版本

使用 target 指定编译到的 JavaScript 版本。


## 实例

不同目标的输出差异：

```javascript
// target: ES5 - 使用 var
var greeting = "Hello";

// target: ES2020 - 使用 let/const
let greeting = "Hello";
```


## 模块系统

配置模块化方案。


## 实例


## 严格模式

strict 选项启用所有严格类型检查。


## 实例

建议：始终启用 strict: true，这是最佳实践。


## 路径别名

配置路径别名简化导入。


## 实例

使用方式：

```text
import Button from "@components/Button";
import { Header } from "@/components";
```


## 文件包含与排除

控制哪些文件包含在编译中。


## 实例


## 常用编译选项一览


## 总结

- tsconfig.json：TypeScript 项目配置文件
- compilerOptions：编译选项核心配置
- include/exclude：控制文件范围
- 路径别名：简化导入路径
- strict: true：始终启用严格模式


## 复习重点

- 能说明 `TypeScript tsconfig.json` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
