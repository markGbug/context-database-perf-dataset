# TypeScript：TypeScript 从 JavaScript 迁移

- 来源：[TypeScript 从 JavaScript 迁移](https://www.runoob.com/typescript/ts-migration.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3175

## 本章内容

将现有 JavaScript 项目逐步迁移到 TypeScript。


## 迁移策略

- 添加 tsconfig.json
- 重命名 .js 为 .ts
- 逐步添加类型注解
- 启用严格模式


## 配置 tsconfig.json


## tsconfig.json


## 逐步启用严格检查


## 分阶段启用


## JSDoc 类型注释

在 JavaScript 中使用 JSDoc 添加类型。


## utils.js

运行结果：

```text
JSDoc 注释添加成功
```


## 类型声明文件

为没有类型定义的模块创建声明。


## src/types/my-module.d.ts


## declare 关键字


## 实例

运行结果：

```text
声明成功
```


## 迁移工具

- tsc --allowJs：编译 JS 文件
- checkJs：检查 JS 类型
- // @ts-check：单文件类型检查
- // @ts-ignore：忽略错误


## legacy.js


## 最佳实践

- 从关键模块开始迁移
- 添加单元测试
- 逐步启用严格模式
- 使用 JSDoc 注释
- 创建类型声明文件


## 总结

- 渐进式：逐步迁移
- JSDoc：类型注释
- 声明文件：.d.ts
- 严格模式：分阶段启用


## 复习重点

- 能说明 `TypeScript 从 JavaScript 迁移` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
