# TypeScript：TypeScript 路径映射 paths

- 来源：[TypeScript 路径映射](https://www.runoob.com/typescript/ts-paths.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3181

## 本章内容

paths 是 tsconfig.json 中的配置选项，用于配置模块路径别名。

它可以让导入路径更简洁，同时保持代码的组织结构清晰。


## 为什么需要路径映射

随着项目规模增长，文件目录会越来越深。

使用相对路径导入文件（如 ../../../components/Button）会让代码难以阅读和维护。

路径映射允许我们使用别名（如 @/components/Button）来替代冗长的相对路径。

别名：路径别名让导入路径更简洁，同时便于调整项目结构。


## 基本配置

在 tsconfig.json 中配置 paths 和 baseUrl。


## tsconfig.json

baseUrl：设置 baseUrl 后，paths 中的路径将相对于此目录解析。


## 使用路径别名

配置完成后，可以在代码中使用别名导入模块。


## src/components/Button.tsx

语法：在 paths 配置中使用 * 作为通配符，导入时用 * 匹配实际路径。


## Webpack 别名配置

如果使用 Webpack，还需要配置 resolve.alias 以支持运行时。


## webpack.config.js

运行时要一致：Webpack 的 alias 配置必须与 TypeScript 的 paths 配置保持一致，否则运行时会出现模块找不到的错误。


## Vite 配置

使用 Vite 时，需要在 tsconfig.json 和 vite.config.ts 中同时配置。


## vite.config.ts

Vite：Vite 使用 Rollup 作为打包引擎，需要在 resolve.alias 中配置别名。


## 多项目路径配置

在 Monorepo 项目中，可以配置跨包的路径别名。


## tsconfig.json (Monorepo)

Monorepo：在 Monorepo 项目中，paths 可以引用其他包的源码路径。


## 注意事项

- baseUrl 必需：paths 需要与 baseUrl 配合使用
- 通配符匹配：使用 * 匹配任意路径
- 保持一致：Webpack/Vite 配置必须与 tsconfig 保持一致
- 相对路径：paths 中的路径是相对于 baseUrl 的

最佳实践：使用路径别名可以让代码更简洁，但不要滥用，建议统一命名规范。


## 总结

路径映射是 TypeScript 项目中管理导入路径的重要工具。

- paths：配置路径别名
- baseUrl：设置基准路径
- 通配符：使用 * 匹配任意字符
- 构建工具：Webpack/Vite 需要同步配置

建议：为常用目录设置路径别名，提高代码可读性和可维护性。


## 复习重点

- 能说明 `TypeScript 路径映射` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
