# Java：Java Number & Math 类

- 来源：[Java Number & Math 类](https://www.runoob.com/java/java-number.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0891

## 本章内容

## Java Number

一般地，当需要使用数字的时候，我们通常使用内置数据类型，如：byte、int、long、double 等。


## 实例

```java
int a = 5000;
float b = 13.65f;
byte c = 0x4a;
```

然而，在实际开发过程中，我们经常会遇到需要使用对象，而不是内置数据类型的情形。为了解决这个问题，Java 语言为每一个内置数据类型提供了对应的包装类。

所有的包装类（Integer、Long、Byte、Double、Float、Short）都是抽象类 Number 的子类。

这种由编译器特别支持的包装称为装箱，所以当内置数据类型被当作对象使用的时候，编译器会把内置类型装箱为包装类。相似的，编译器也可以把一个对象拆箱为内置类型。

Number 类属于 java.lang 包。

Number 是一个抽象类，主要作用是为各种数值类型提供统一的转换方法：


## 实例

下面是一个使用 Integer 对象的实例：


## Test.java 文件代码：

```java
public class Test{

   public static void main(String[] args){
      Integer x = 5;
      x =  x + 10;
      System.out.println(x);
   }
}
```

以上实例编译运行结果如下：

```text
15
```

当 x 被赋为整型值时，由于x是一个对象，所以编译器要对x进行装箱。然后，为了使x能进行加运算，所以要对x进行拆箱。


### 常用方法示例


## 实例


## 实例


### 特殊数值处理


## 实例


## 实例


### 自动装箱与拆箱

Java 5+ 支持自动转换：


## 实例


## Java Math 类

Math 类是 Java 提供的数学工具类，位于 java.lang 包中，包含执行基本数值运算的静态方法。

Java 的 Math 包含了用于执行基本数学运算的属性和方法，如初等指数、对数、平方根和三角函数。

Math 的方法都被定义为 static 形式，通过 Math 类可以在主函数中直接调用。


## Test.java 文件代码：

```java
public class Test {
    public static void main (String []args)
    {
        System.out.println("90 度的正弦值：" + Math.sin(Math.PI/2));
        System.out.println("0度的余弦值：" + Math.cos(0));
        System.out.println("60度的正切值：" + Math.tan(Math.PI/3));
        System.out.println("1的反正切值： " + Math.atan(1));
        System.out.println("π/2的角度值：" + Math.toDegrees(Math.PI/2));
        System.out.println(Math.PI);
    }
}
```

以上实例编译运行结果如下：

```text
90 度的正弦值：1.0
0度的余弦值：1.0
60度的正切值：1.7320508075688767
1的反正切值： 0.7853981633974483
π/2的角度值：90.0
3.141592653589793
```


### 高级数学运算


## 实例


## 实例


## 实例


## 实例


## Number & Math 类方法

下面的表中列出的是 Number & Math 类常用的一些方法：


## Math 的 floor,round 和 ceil 方法实例比较


## floor,round 和 ceil 实例：

```java
public class Main {
  public static void main(String[] args) {
    double[] nums = { 1.4, 1.5, 1.6, -1.4, -1.5, -1.6 };
    for (double num : nums) {
      test(num);
    }
  }

  private static void test(double num) {
    System.out.println("Math.floor(" + num + ")=" + Math.floor(num));
    System.out.println("Math.round(" + num + ")=" + Math.round(num));
    System.out.println("Math.ceil(" + num + ")=" + Math.ceil(num));
  }
}
```

以上实例执行输出结果为：

```text
Math.floor(1.4)=1.0
Math.round(1.4)=1
Math.ceil(1.4)=2.0
Math.floor(1.5)=1.0
Math.round(1.5)=2
Math.ceil(1.5)=2.0
Math.floor(1.6)=1.0
Math.round(1.6)=2
Math.ceil(1.6)=2.0
Math.floor(-1.4)=-2.0
Math.round(-1.4)=-1
Math.ceil(-1.4)=-1.0
Math.floor(-1.5)=-2.0
Math.round(-1.5)=-1
Math.ceil(-1.5)=-1.0
Math.floor(-1.6)=-2.0
Math.round(-1.6)=-2
Math.ceil(-1.6)=-1.0
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java Number & Math 类` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
