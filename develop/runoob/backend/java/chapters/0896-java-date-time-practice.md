# Java：Java 日期时间

- 来源：[Java 日期时间](https://www.runoob.com/java/java-date-time.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0896

## 本章内容

Java 提供了多套日期时间 API，以下是主要类别的对比和常用方法总结：


## LocalDate/DateTimeFormatter

LocalDate/DateTimeFormatter 是 Java 8 引入的日期类，LocalDate 用于表示不带时间的日期（年-月-日），DateTimeFormatter 用于格式化和解析日期时间对象。


## 实例

以上实例输出结果为：

```text
当前日期: 2025-05-01
国庆节: 2025-10-01
明天: 2025-05-02
下个月: 2025-06-01
去年今天: 2024-05-01
```

- 新项目优先使用 java.time 包 (Java 8+)
- 避免使用老旧的 Date 和 Calendar 类
- 明确区分使用时区： 不需要时区：LocalDate/LocalTime/LocalDateTime 需要时区：ZonedDateTime
- 格式化时考虑线程安全：使用 DateTimeFormatter 而非 SimpleDateFormat
- 数据库交互： JDBC 4.2+ 直接支持 java.time 类型 旧版本可转换为 java.sql.Date/Timestamp

1. LocalDate (日期)


## 实例

2. LocalTime (时间)


## 实例

3. LocalDateTime (日期时间)


## 实例

4. ZonedDateTime (带时区日期时间)


## 实例

5. Instant (时间戳)


## 实例


## Date 类

java.util 包提供了 Date 类来封装当前的日期和时间。 Date 类提供两个构造函数来实例化 Date 对象。

第一个构造函数使用当前日期和时间来初始化对象。

```text
Date( )
```

第二个构造函数接收一个参数，该参数是从 1970 年 1 月 1 日起的毫秒数。

```text
Date(long millisec)
```

Date 对象创建以后，可以调用下面的方法。


## 获取当前日期时间

Java中获取当前日期和时间很简单，使用 Date 对象的 toString() 方法来打印当前日期和时间，如下所示：


## 实例

```java
import java.util.Date;

public class DateDemo {
   public static void main(String[] args) {
       // 初始化 Date 对象
       Date date = new Date();

       // 使用 toString() 函数显示日期时间
       System.out.println(date.toString());
   }
}
```

以上实例编译运行结果如下:

```text
Mon May 04 09:51:52 CDT 2013
```


## 日期比较

Java 使用以下三种方法来比较两个日期：

- 使用 getTime() 方法获取两个日期（自1970年1月1日经历的毫秒数值），然后比较这两个值。
- 使用方法 before()，after() 和 equals()。例如，一个月的 12 号比 18 号早，则 new Date(99, 2, 12).before(new Date (99, 2, 18)) 返回true。
- 使用 compareTo() 方法，它是由 Comparable 接口定义的，Date 类实现了这个接口。


### 1. 使用 getTime() 方法比较

这种方法通过比较日期对象自 1970年1月1日（Unix纪元）以来的毫秒数。


## 实例

输出：

```text
date1 在 date2 之前
```


### 2. 使用 before(), after() 和 equals() 方法

这些方法是 Date 类自带的比较方法，语义更清晰。


## 实例

输出：

```text
date1 在 date2 之前吗？ true
date1 在 date2 之后吗？ false
两个日期相同吗？ false
```


### 3. 使用 compareTo() 方法

Date 类实现了 Comparable 接口，可以使用 compareTo() 方法进行比较。


## 实例

输出：

```text
date1 在 date2 之前
```


## 使用 SimpleDateFormat 格式化日期

SimpleDateFormat 是一个以语言环境敏感的方式来格式化和分析日期的类。SimpleDateFormat 允许你选择任何用户自定义日期时间格式来运行。例如：


## 实例

```java
import  java.util.*;
import java.text.*;

public class DateDemo {
   public static void main(String[] args) {

      Date dNow = new Date( );
      SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd hh:mm:ss");

      System.out.println("当前时间为: " + ft.format(dNow));
   }
}
```

```text
SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd hh:mm:ss");
```

这一行代码确立了转换的格式，其中 yyyy 是完整的公元年，MM 是月份，dd 是日期，HH:mm:ss 是时、分、秒。

注意:有的格式大写，有的格式小写，例如 MM 是月份，mm 是分；HH 是 24 小时制，而 hh 是 12 小时制。

以上实例编译运行结果如下:

```text
当前时间为: 2018-09-06 10:16:34
```


## 日期和时间的格式化编码

时间模式字符串用来指定时间格式。在此模式中，所有的 ASCII 字母被保留为模式字母，定义如下：


## 使用printf格式化日期

printf 方法可以很轻松地格式化时间和日期。使用两个字母格式，它以 %t 开头并且以下面表格中的一个字母结尾。

- %tY：输出四位数的年份，例如：2023
- %ty：输出两位数的年份，例如：23
- %tm：输出两位数的月份，例如：02
- %tB：输出月份的全名，例如：February
- %tb：输出月份的缩写，例如：Feb
- %tA：输出星期的全名，例如：Wednesday
- %ta：输出星期的缩写，例如：Wed
- %td：输出两位数的日期，例如：24
- %te：输出一位或两位数的日期，例如：24 或 02
- %tH：输出24小时制的小时数，例如：23
- %tI：输出12小时制的小时数，例如：11
- %tM：输出分钟数，例如：45
- %tS：输出秒数，例如：30
- %tp：输出上午还是下午，例如：AM 或 PM
- %tZ：输出时区，例如：GMT+08:00

转换符

说明

示例

%tc

包括全部日期和时间信息

星期六 十月 27 14:21:20 CST 2007

%tF

"年-月-日"格式

2007-10-27

%tD

"月/日/年"格式

10/27/07


### 实例


## 实例

执行输出结果为：

```text
2023-02-24 13:34:45 GMT+08:00
```


## 实例

```java
import java.util.Date;

public class DateDemo {

  public static void main(String[] args) {
     // 初始化 Date 对象
     Date date = new Date();

     //c的使用
    System.out.printf("全部日期和时间信息：%tc%n",date);
    //f的使用
    System.out.printf("年-月-日格式：%tF%n",date);
    //d的使用
    System.out.printf("月/日/年格式：%tD%n",date);
    //r的使用
    System.out.printf("HH:MM:SS PM格式（12时制）：%tr%n",date);
    //t的使用
    System.out.printf("HH:MM:SS格式（24时制）：%tT%n",date);
    //R的使用
    System.out.printf("HH:MM格式（24时制）：%tR",date);
  }
}
```

以上实例编译运行结果如下:

```text
全部日期和时间信息：星期一 九月 10 10:43:36 CST 2012
年-月-日格式：2012-09-10
月/日/年格式：09/10/12
HH:MM:SS PM格式（12时制）：10:43:36 上午
HH:MM:SS格式（24时制）：10:43:36
HH:MM格式（24时制）：10:43
```

如果你需要重复提供日期，那么利用这种方式来格式化它的每一部分就有点复杂了。因此，可以利用一个格式化字符串指出要被格式化的参数的索引。

索引必须紧跟在 % 后面，而且必须以 $ 结束。例如：


## 后续章节

- 实例
- 实例
- 实例
- 解析字符串为时间
- 实例
- Java 休眠(sleep)
- 实例
- 测量时间
- 实例
- Calendar类
- 创建一个代表系统当前日期的Calendar对象
- 创建一个指定日期的Calendar对象
- Calendar类对象字段类型
- Calendar类对象信息的设置
- Calendar类对象信息的获得
- GregorianCalendar类

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java 日期时间` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
