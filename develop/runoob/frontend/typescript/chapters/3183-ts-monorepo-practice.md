# TypeScript：TypeScript Monorepo 配置

- 来源：[TypeScript Monorepo 配置](https://www.runoob.com/typescript/ts-monorepo.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3183

## 本章内容

Monorepo 是一种将多个项目放在同一个代码仓库中的开发模式。

TypeScript 通过项目引用和工具链支持 Monorepo，可以高效管理多个包。


## 为什么需要 Monorepo

当项目包含多个包（如工具库、组件库、应用程序）时，传统方式需要维护多个代码仓库。

Monorepo 将所有包放在同一个仓库中，共享代码更方便，版本管理更统一。

TypeScript 的项目引用功能让 Monorepo 项目的类型检查和构建更高效。

概念：Monorepo（单一仓库）将多个相关项目放在同一个代码仓库中，便于代码共享和协调开发。


## pnpm Workspace

pnpm 是现代的包管理器，原生支持 Workspace 功能。


## 根目录 package.json

pnpm：pnpm 的 Workspace 功能可以自动将 packages 目录下的包链接在一起。


## 项目结构

创建 Monorepo 项目的目录结构。


## 目录结构

packages：所有包都放在 packages 目录下，每个包有独立的 package.json 和 tsconfig.json。


## 基础 TypeScript 配置

创建基础配置供所有包使用。


## tsconfig.base.json

继承：各包的 tsconfig.json 继承基础配置，只覆盖需要自定义的选项。


## 工具包配置

为工具包配置 TypeScript。


## packages/utils/tsconfig.json

composite：启用项目引用后，TypeScript 可以增量编译此包。


## 应用程序配置

为主应用程序配置 TypeScript 并引用其他包。


## packages/app/tsconfig.json

路径别名：可以配置路径别名直接引用同仓库的其他包。


## 包之间的依赖

在 package.json 中声明对同仓库包的依赖。


## packages/app/package.json

workspace：使用 workspace:* 指向同仓库的其他包，pnpm 会自动解析。


## 构建脚本

为 Monorepo 创建统一的构建脚本。


## 根目录 package.json

pnpm -r：递归执行所有包的同名脚本。


## 注意事项

- 包命名规范：使用 @org-name/package 格式
- 独立版本：每个包可以独立版本管理
- workspace 协议：使用 workspace:* 引用同仓库包
- 构建顺序：被依赖的包需要先构建

最佳实践：Monorepo 适合管理多个相关项目，可以显著提高代码复用和开发效率。


## 总结

Monorepo 是现代前端项目管理的推荐模式。

- pnpm Workspace：原生支持 Monorepo
- 项目引用：实现增量编译
- 路径别名：便捷引用同仓库包
- 统一管理：共享配置和依赖

建议：当项目包含多个相关包时，优先考虑 Monorepo 方案。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript Monorepo 配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
