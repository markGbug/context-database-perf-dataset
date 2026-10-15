# Python 设计模式：Python 设计模式

- 来源：[Python 设计模式](https://www.runoob.com/python-design-pattern/python-design-pattern-intro.html)
- 分类：计算机基础
- 技术：Python 设计模式
- 笔记类型：练习笔记
- 章节序号：1379

## 本章内容

设计模式是软件开发中针对常见问题的可重用解决方案。它们不是可以直接转换为代码的完整设计，而是解决特定问题的模板或蓝图。


### 设计模式的核心价值

设计模式就像建筑领域的标准图纸，为软件开发提供了以下好处：

- 提高代码复用性：避免重复造轮子
- 增强代码可维护性：使代码结构更清晰
- 促进团队协作：提供统一的编程语言和思维方式
- 提升代码质量：经过实践检验的解决方案更可靠


### 生活中的设计模式类比

想象你要建造一栋房子：

- 原始方式：每次从零开始设计，容易出错且效率低下
- 使用设计模式：使用标准的建筑图纸，知道客厅、厨房、卧室的标准布局方式

设计模式就是软件开发的"标准建筑图纸"。


## 设计模式的类型

根据经典著作 《Design Patterns - Elements of Reusable Object-Oriented Software》（中文译名：《设计模式：可复用的面向对象软件元素》） 的定义， 共有 23 种经典设计模式。这些模式按其关注点可分为三大类： 创建型模式（Creational Patterns）、结构型模式（Structural Patterns）和行为型模式（Behavioral Patterns）。 此外，在企业级开发中，还有一类常用的架构级设计模式。

- 工厂模式（Factory Pattern）
- 抽象工厂模式（Abstract Factory Pattern）
- 单例模式（Singleton Pattern）
- 建造者模式（Builder Pattern）
- 原型模式（Prototype Pattern）
- 适配器模式（Adapter Pattern）
- 桥接模式（Bridge Pattern）
- 过滤器模式（Filter / Criteria Pattern）
- 组合模式（Composite Pattern）
- 装饰器模式（Decorator Pattern）
- 外观模式（Facade Pattern）
- 享元模式（Flyweight Pattern）
- 代理模式（Proxy Pattern）
- 责任链模式（Chain of Responsibility Pattern）
- 命令模式（Command Pattern）
- 解释器模式（Interpreter Pattern）
- 迭代器模式（Iterator Pattern）
- 中介者模式（Mediator Pattern）
- 备忘录模式（Memento Pattern）
- 观察者模式（Observer Pattern）
- 状态模式（State Pattern）
- 空对象模式（Null Object Pattern）
- 策略模式（Strategy Pattern）
- 模板方法模式（Template Method Pattern）
- 访问者模式（Visitor Pattern）
- MVC 模式（Model-View-Controller Pattern）
- 业务代表模式（Business Delegate Pattern）


## 设计模式的优点

- 提供统一的设计语言，使开发者能快速沟通设计意图。
- 为常见问题提供成熟、可复用的解决方案。
- 降低系统耦合度，提高代码的可维护性与可扩展性。
- 减少重复设计，提升开发效率与代码质量。
- 帮助新成员快速理解系统架构与设计思想。


## 设计模式的六大原则

1、开闭原则（Open-Closed Principle）

对扩展开放，对修改关闭。软件应能通过扩展新功能，而非修改已有代码来适应变化。实现这一原则的核心在于使用抽象（接口或基类）定义稳定的行为。

2、里氏替换原则（Liskov Substitution Principle）

任何基类出现的地方，子类都应该可以替代。只有当派生类能完全替代基类时，继承才有意义。这一原则保证了多态的正确性，是开闭原则的重要补充。

3、依赖倒置原则（Dependency Inversion Principle）

高层模块不应依赖低层模块，两者都应依赖抽象。具体实现应依赖接口或抽象类，而不是直接依赖具体类。该原则使系统更易于扩展与测试。

4、接口隔离原则（Interface Segregation Principle）

一个类不应该依赖它不需要的接口。应将大接口拆分为多个更小、更专用的接口，以降低耦合、提高灵活性。

5、迪米特法则（Law of Demeter）

又称"最少知道原则"：一个对象应尽量减少与其他对象的交互。换言之，一个类应只了解与自己直接相关的对象，从而降低系统复杂度。

6、合成复用原则（Composite Reuse Principle）

优先使用组合或聚合关系来实现复用，而非继承。继承会造成强耦合，而组合能在运行时灵活替换依赖，实现更优雅的结构设计。


## Python 中常用的设计模式示例

让我们通过几个具体的例子来理解设计模式在 Python 中的应用。


### 单例模式（Singleton）

单例模式确保一个类只有一个实例，并提供一个全局访问点。


## 实例

应用场景：

- 数据库连接池
- 配置管理器
- 日志记录器


### 工厂模式（Factory）

工厂模式提供创建对象的接口，让子类决定实例化哪个类。


## 实例

代码说明：

- Notification 是抽象基类，定义接口
- EmailNotification 和 SMSNotification 是具体实现
- NotificationFactory 负责创建具体的通知对象


### 观察者模式（Observer）

观察者模式定义对象间的一对多依赖关系，当一个对象状态改变时，所有依赖它的对象都会得到通知。


## 实例


## 设计模式在 Python 中的特殊考虑


### Python 的动态特性

Python 作为动态语言，有些设计模式实现起来更简单：


## 实例


### 装饰器模式的内置支持

Python 内置了装饰器语法，让装饰器模式实现更优雅：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 设计模式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
