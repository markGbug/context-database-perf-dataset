# Java：Java Character 类

- 来源：[Java Character 类](https://www.runoob.com/java/java-character.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0892

## 本章内容

Character 类用于对单个字符进行操作。

Character 类在对象中包装一个基本类型 char 的值


## 实例

```text
char ch = 'a';

// Unicode 字符表示形式
char uniChar = '\u039A';

// 字符数组
char[] charArray ={ 'a', 'b', 'c', 'd', 'e' };
```

然而，在实际开发过程中，我们经常会遇到需要使用对象，而不是内置数据类型的情况。为了解决这个问题，Java语言为内置数据类型char提供了包装类Character类。

Character类提供了一系列方法来操纵字符。你可以使用Character的构造方法创建一个Character类对象，例如：

```text
Character ch = new Character('a');
```

在某些情况下，Java编译器会自动创建一个Character对象。

例如，将一个char类型的参数传递给需要一个Character类型参数的方法时，那么编译器会自动地将char类型参数转换为Character对象。 这种特征称为装箱，反过来称为拆箱。


## 实例

```text
// 原始字符 'a' 装箱到 Character 对象 ch 中
Character ch = 'a';

// 原始字符 'x' 用 test 方法装箱
// 返回拆箱的值到 'c'
char c = test('x');
```


## 转义序列

前面有反斜杠（\）的字符代表转义字符，它对编译器来说是有特殊含义的。

下面列表展示了Java的转义序列：


### 实例

当打印语句遇到一个转义序列时，编译器可以正确地对其进行解释。

以下实例转义双引号并输出：


## Test.java 文件代码：

```java
public class Test {

   public static void main(String[] args) {
      System.out.println("访问\"菜鸟教程!\"");
   }
}
```

以上实例编译运行结果如下：

```text
访问"菜鸟教程!"
```


## Character 方法

下面是Character类的方法：

对于方法的完整列表，请参考的 java.lang.Character API 规范。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java Character 类` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
