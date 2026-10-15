# TypeScript：TypeScript 单元测试

- 来源：[TypeScript 单元测试](https://www.runoob.com/typescript/ts-unit-testing.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3176

## 本章内容

TypeScript 项目中的单元测试实践，确保代码质量。

单元测试可以验证代码的正确性，TypeScript 的类型系统与测试框架完美结合，可以编写类型安全的测试代码。


## 为什么需要单元测试

单元测试是保证代码质量的重要手段，它可以验证代码的正确性，防止 bug 出现。

TypeScript 项目中，测试代码同样受益于类型系统：类型错误会在编译时被发现，IDE 提供智能提示，测试代码更可靠。

此外，测试代码也是最好的文档，可以通过测试了解函数/类的预期行为。

质量保障：单元测试可以快速发现回归问题，确保代码改动不会破坏现有功能。


## 测试框架配置

Jest 是 TypeScript 项目最流行的测试框架。


## 安装 Jest

ts-jest：这是一个预处理器，让 Jest 能够直接运行 TypeScript 文件，无需手动编译。


## 配置 jest.config.js

配置 Jest 测试环境。


## jest.config.js

配置说明：测试文件通常放在 __tests__ 目录或以 .test.ts 结尾。


## 测试函数

首先编写需要测试的业务代码。


## src/utils/calculator.ts

然后编写对应的测试代码。


## src/utils/calculator.test.ts

运行结果：

```text
Calculator
  add
    ✓ should add two numbers
    ✓ should handle negative numbers
  divide
    ✓ should divide two numbers
    ✓ should throw error when dividing by zero
```

describe/it：describe 用于分组测试，it（或 test）用于定义单个测试用例。


## 测试 Service

测试 Service 层的业务逻辑。


## src/services/userService.ts


## src/services/userService.test.ts

运行结果：

```text
UserService
  createUser
    ✓ should create a user with id
    ✓ should increment id for each user
  getUser
    ✓ should return user by id
    ✓ should return undefined for non-existent id
```

测试隔离：每个测试用例应该独立，使用 beforeEach 确保每个测试都有干净的状态。


## Mock

使用 Mock 模拟依赖，如外部 API、数据库等。


## 实例

运行结果：

```text
✓ mock 函数被调用 3 次
```

Mock 用途：当测试的代码依赖外部系统时，使用 Mock 可以隔离依赖，只测试目标代码的逻辑。


## 注意事项

- 测试文件位置：放在 __tests__ 目录或使用 .test.ts 后缀
- 测试命名：使用描述性的测试名称，说明预期行为
- 独立测试：每个测试应该独立运行，不依赖其他测试
- 覆盖率：关注核心业务逻辑的测试覆盖率

最佳实践：测试应该快速、可靠、相互独立。遵循 AAA 原则：Arrange（准备）、Act（执行）、Assert（断言）。


## 总结

单元测试是保证 TypeScript 代码质量的重要手段。

- Jest：最流行的 TypeScript 测试框架
- describe：用于分组相关测试
- it/test：定义单个测试用例
- expect：断言测试结果
- Mock：模拟外部依赖

建议：为关键业务逻辑编写测试，确保代码改动不会引入 bug。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 单元测试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
