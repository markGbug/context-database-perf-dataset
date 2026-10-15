# TypeScript：TypeScript 性能优化

- 来源：[TypeScript 性能优化](https://www.runoob.com/typescript/ts-performance.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3185

## 本章内容

TypeScript 项目的性能优化涉及编译速度、运行时性能和代码体积等多个方面。

本教程介绍常见的性能优化技巧，帮助构建更高效的 TypeScript 应用。


## 为什么需要性能优化

TypeScript 虽然提供了强大的类型系统，但使用不当会影响编译速度和运行性能。

大型项目的编译可能需要数分钟，严重影响开发体验。

本教程介绍的配置和技巧可以显著提升 TypeScript 项目的性能。

优化目标：更快的编译速度、更小的打包体积、更高的运行时性能。


## 编译配置优化

通过优化 tsconfig.json 配置来提升编译速度。


## tsconfig.json 优化配置

skipLibCheck：这是最重要的优化选项，可以将编译时间减少 50% 以上。


## 项目引用优化

使用项目引用将大型项目拆分为小模块，实现增量编译。


## packages/utils/tsconfig.json

composite：启用后，TypeScript 会生成 .tsbuildinfo 文件来加速后续编译。


## 类型推断优化

充分利用 TypeScript 的类型推断，避免过度标注。

减少标注：TypeScript 的类型推断已经很智能，大部分情况下不需要显式标注类型。


## 避免使用 any

使用 any 会失去类型检查的优势，影响运行时性能。


## 实例

unknown vs any：unknown 是类型安全的 any，使用前需要进行类型检查。


## 接口 vs 类型别名

根据场景选择合适的类型定义方式。


## 实例

选择建议：对象类型使用接口，联合类型使用 type，功能类型使用 type。


## 构建工具优化

配置构建工具以获得最佳性能。


## vite.config.ts

代码分割：使用 manualChunks 将大型库分离，减少主包体积。


## Tree Shaking

配置模块以支持 Tree Shaking，消除未使用的代码。


## src/utils/index.ts

具名导出：使用具名导出而不是默认导出，可以让构建工具更好地进行 Tree Shaking。


## 注意事项

- skipLibCheck：生产环境必须开启
- 增量编译：开发环境建议开启
- 避免 any：使用 unknown 代替
- Tree Shaking：使用 ES 模块和具名导出

最佳实践：在开发初期就设置好优化配置，避免后期重构。


## 总结

TypeScript 性能优化涉及多个方面。

- 编译优化：skipLibCheck、incremental、project references
- 类型优化：利用推断、避免 any、选择合适的类型定义
- 构建优化：代码分割、Tree Shaking、依赖优化
- 运行时优化：类型安全、泛型约束

建议：定期检查编译时间和包体积，持续优化项目性能。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 性能优化` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
