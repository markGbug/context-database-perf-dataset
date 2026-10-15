# Java：Java 对象和类

- 来源：[Java 对象和类](https://www.runoob.com/java/java-object-classes.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0882

## 本章内容

Java 作为一种面向对象的编程语言，支持以下基本概念：

1、类（Class）：

- 定义对象的蓝图，包括属性和方法。
- 示例：public class Car { ... }

2、对象（Object）：

- 类的实例，具有状态和行为。
- 示例：Car myCar = new Car();

3、继承（Inheritance）：

- 一个类可以继承另一个类的属性和方法。
- 示例：public class Dog extends Animal { ... }

4、封装（Encapsulation）：

- 将对象的状态（字段）私有化，通过公共方法访问。
- 示例：private String name; public String getName() { return name; }

5、多态（Polymorphism）：

- 对象可以表现为多种形态，主要通过方法重载和方法重写实现。
- 示例： 方法重载：public int add(int a, int b) { ... } 和 public double add(double a, double b) { ... } 方法重写：@Override public void makeSound() { System.out.println("Meow"); }

6、抽象（Abstraction）：

- 使用抽象类和接口来定义必须实现的方法，不提供具体实现。


## Java中的对象


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java 对象和类` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
