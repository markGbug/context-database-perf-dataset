# Java：Java 反射（Reflection）

- 来源：[Java 反射](https://www.runoob.com/java/java-reflection.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0911

## 本章内容

Java 反射（Reflection）是一个强大的特性，它允许程序在运行时查询、访问和修改类、接口、字段和方法的信息。反射提供了一种动态地操作类的能力，这在很多框架和库中被广泛使用，例如Spring框架的依赖注入。


### 反射 API

Java 的反射 API 提供了一系列的类和接口来操作 Class 对象。主要的类包括：

- java.lang.Class：表示类的对象。提供了方法来获取类的字段、方法、构造函数等。
- java.lang.reflect.Field：表示类的字段（属性）。提供了访问和修改字段的能力。
- java.lang.reflect.Method：表示类的方法。提供了调用方法的能力。
- java.lang.reflect.Constructor：表示类的构造函数。提供了创建对象的能力。


### 工作流程

- 获取 Class 对象：首先获取目标类的 Class 对象。
- 获取成员信息：通过 Class 对象，可以获取类的字段、方法、构造函数等信息。
- 操作成员：通过反射 API 可以读取和修改字段的值、调用方法以及创建对象。

以下是 Java 反射的基本使用方式及其常见应用。


### 1. 获取 Class 对象

每个类在 JVM 中都有一个与之相关的 Class 对象。可以通过以下方式获取 Class 对象：

通过类字面量

```text
Class<?> clazz = String.class;
```

通过对象实例：

```text
String str = "Hello";
Class<?> clazz = str.getClass();
```

通过 Class.forName() 方法：

```text
Class<?> clazz = Class.forName("java.lang.String");
```


### 2. 创建对象

可以使用反射动态创建对象：

```text
Class<?> clazz = Class.forName("java.lang.String");
Object obj = clazz.getDeclaredConstructor().newInstance();
```


### 3. 访问字段

可以通过反射访问和修改类的字段：

```text
Class<?> clazz = Person.class;
Field field = clazz.getDeclaredField("name");
field.setAccessible(true); // 如果字段是私有的，需要设置为可访问
Object value = field.get(personInstance); // 获取字段值
field.set(personInstance, "New Name"); // 设置字段值
```


### 4. 调用方法

可以通过反射调用类的方法：

```text
Class<?> clazz = Person.class;
Method method = clazz.getMethod("sayHello");
method.invoke(personInstance);

Method methodWithArgs = clazz.getMethod("greet", String.class);
methodWithArgs.invoke(personInstance, "World");
```


### 5. 获取构造函数

可以使用反射获取和调用构造函数：

```text
Class<?> clazz = Person.class;
Constructor<?> constructor = clazz.getConstructor(String.class, int.class);
Object obj = constructor.newInstance("John", 30);
```


### 6. 获取接口和父类

可以使用反射获取类实现的接口和父类：

```java
Class<?> clazz = Person.class;

// 获取所有接口
Class<?>[] interfaces = clazz.getInterfaces();
for (Class<?> i : interfaces) {
    System.out.println("Interface: " + i.getName());
}

// 获取父类
Class<?> superClass = clazz.getSuperclass();
System.out.println("Superclass: " + superClass.getName());
```

以下是一个完整的示例，展示了如何使用反射来创建对象、访问字段和调用方法：


## 实例

编译执行以上代码，输出结果为：

```text
Name: John
Updated Name: Doe
Doe says: World
```


## java.lang.reflect

java.lang.reflect 是 Java 反射机制的核心包，提供了操作类及其成员（字段、方法、构造函数等）的类和接口。通过这些 API，开发者可以在运行时动态地查询和修改类的结构。

以下是 java.lang.reflect 包中的主要类和接口的详细介绍：


### 1. Class 类

- 功能：表示类的对象，提供了获取类信息的方法，如字段、方法、构造函数等。
- 主要方法：getFields()：获取所有公共字段。getDeclaredFields()：获取所有声明的字段，包括私有字段。getMethods()：获取所有公共方法。getDeclaredMethods()：获取所有声明的方法，包括私有方法。getConstructors()：获取所有公共构造函数。getDeclaredConstructors()：获取所有声明的构造函数，包括私有构造函数。getSuperclass()：获取类的父类。getInterfaces()：获取类实现的所有接口。


### 2. Field 类

- 功能：表示类的字段（属性），提供了访问和修改字段值的方法。
- 主要方法：get(Object obj)：获取指定对象的字段值。set(Object obj, Object value)：设置指定对象的字段值。getType()：获取字段的数据类型。getModifiers()：获取字段的修饰符（如 public、private）。


### 3. Method 类

- 功能：表示类的方法，提供了调用方法的能力。
- 主要方法：invoke(Object obj, Object... args)：调用指定对象的方法。getReturnType()：获取方法的返回类型。getParameterTypes()：获取方法的参数类型。getModifiers()：获取方法的修饰符（如 public、private）。


### 4. Constructor 类

- 功能：表示类的构造函数，提供了创建对象的能力。
- 主要方法：newInstance(Object... initargs)：创建一个新实例，使用指定的构造函数参数。getParameterTypes()：获取构造函数的参数类型。getModifiers()：获取构造函数的修饰符（如 public、private）。


### 示例代码

以下是使用 java.lang.reflect 包进行反射操作的示例：


## 实例

编译执行以上代码，输出结果为：

```text
Original Model: Toyota
Original Year: 2020
Updated Model: Honda
Updated Year: 2024
The Honda car of year 2024 is starting.
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java 反射` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
