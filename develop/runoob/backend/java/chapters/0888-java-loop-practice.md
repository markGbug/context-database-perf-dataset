# Java：Java 循环结构学习笔记

- 来源：[Java 循环结构](https://www.runoob.com/java/java-loop.html)
- 分类：后端开发
- 技术：Java
- 章节序号：0888

## 本章要点

Java 的循环结构用于重复执行一段代码，直到循环条件不再满足。菜鸟教程这一章主要覆盖 6 个点：

- `while` 循环
- `do...while` 循环
- `for` 循环
- 增强 `for` 循环
- `break` 关键字
- `continue` 关键字

选择循环结构时，核心判断是：循环次数是否明确、是否至少要执行一次、是否只是遍历数组或集合。

## while 循环

`while` 会先判断布尔表达式，只有表达式为 `true` 才会进入循环体。

```java
while (布尔表达式) {
    // 循环内容
}
```

只要布尔表达式一直为 `true`，循环就会一直执行。因此在循环体中通常要修改参与判断的变量，否则容易出现死循环。

示例：

```java
public class Test {
    public static void main(String[] args) {
        int x = 10;

        while (x < 20) {
            System.out.print("value of x : " + x);
            x++;
            System.out.print("\n");
        }
    }
}
```

输出：

```text
value of x : 10
value of x : 11
value of x : 12
value of x : 13
value of x : 14
value of x : 15
value of x : 16
value of x : 17
value of x : 18
value of x : 19
```

执行过程：

1. 初始化 `x = 10`。
2. 判断 `x < 20`，为 `true` 时执行循环体。
3. 输出当前 `x`。
4. 执行 `x++`，让循环条件逐步接近结束。
5. 当 `x` 变为 `20` 时，`x < 20` 为 `false`，循环停止。

## do...while 循环

`do...while` 会先执行循环体，再判断布尔表达式。因此它至少执行一次。

```java
do {
    // 代码语句
} while (布尔表达式);
```

注意结尾有分号 `;`。这是 `do...while` 和普通 `while` 在语法上的一个明显区别。

示例：

```java
public class Test {
    public static void main(String[] args) {
        int x = 10;

        do {
            System.out.print("value of x : " + x);
            x++;
            System.out.print("\n");
        } while (x < 20);
    }
}
```

输出同样是 `10` 到 `19`：

```text
value of x : 10
value of x : 11
value of x : 12
value of x : 13
value of x : 14
value of x : 15
value of x : 16
value of x : 17
value of x : 18
value of x : 19
```

`while` 与 `do...while` 的关键区别：

| 结构 | 判断时机 | 循环体至少执行一次 |
| --- | --- | --- |
| `while` | 执行前判断 | 不一定 |
| `do...while` | 执行后判断 | 是 |

如果一开始条件就是 `false`，`while` 一次都不执行，而 `do...while` 仍会先执行一次循环体。

## for 循环

`for` 循环适合循环次数在执行前就比较明确的场景。

```java
for (初始化; 布尔表达式; 更新) {
    // 代码语句
}
```

执行顺序：

1. 先执行初始化语句，可以声明并初始化一个或多个循环控制变量，也可以为空。
2. 判断布尔表达式。
3. 如果表达式为 `true`，执行循环体。
4. 循环体执行完后，执行更新语句。
5. 再次判断布尔表达式，重复上面的过程。
6. 如果表达式为 `false`，循环结束，继续执行循环后面的语句。

示例：

```java
public class Test {
    public static void main(String[] args) {
        for (int x = 10; x < 20; x = x + 1) {
            System.out.print("value of x : " + x);
            System.out.print("\n");
        }
    }
}
```

输出：

```text
value of x : 10
value of x : 11
value of x : 12
value of x : 13
value of x : 14
value of x : 15
value of x : 16
value of x : 17
value of x : 18
value of x : 19
```

这段代码中：

- `int x = 10` 是初始化，只执行一次。
- `x < 20` 是循环条件，每轮循环前判断。
- `x = x + 1` 是更新语句，每轮循环体结束后执行。

## 增强 for 循环

Java 5 引入了增强 `for` 循环，主要用于遍历数组，也常用于遍历集合。

```java
for (声明语句 : 表达式) {
    // 代码语句
}
```

其中：

- 声明语句：声明一个新的局部变量，类型必须和数组元素类型匹配。
- 表达式：要访问的数组名，或者返回值为数组的方法。
- 循环变量的作用域限定在循环语句块内。
- 每次迭代时，循环变量的值等于当前数组元素的值。

示例：

```java
public class Test {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        for (int x : numbers) {
            System.out.print(x);
            System.out.print(",");
        }

        System.out.print("\n");

        String[] names = {"James", "Larry", "Tom", "Lacy"};

        for (String name : names) {
            System.out.print(name);
            System.out.print(",");
        }
    }
}
```

输出：

```text
10,20,30,40,50,
James,Larry,Tom,Lacy,
```

增强 `for` 的优点是写法简洁，特别适合“只需要读取每个元素”的遍历场景。如果需要下标、需要倒序、需要跳步，普通 `for` 更合适。

## break 关键字

`break` 主要用在循环语句或 `switch` 语句中，用来跳出整个语句块。

在循环中，`break` 会跳出最里层循环，并继续执行循环后面的语句。

```java
break;
```

示例：

```java
public class Test {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        for (int x : numbers) {
            // x 等于 30 时跳出循环
            if (x == 30) {
                break;
            }

            System.out.print(x);
            System.out.print("\n");
        }
    }
}
```

输出：

```text
10
20
```

原因：

- 当 `x = 10`、`x = 20` 时，正常输出。
- 当 `x = 30` 时满足 `if (x == 30)`，执行 `break`。
- `break` 直接结束整个循环，所以 `30`、`40`、`50` 都不会输出。

## continue 关键字

`continue` 用于循环控制结构中，作用是跳过本次循环剩余语句，直接进入下一次迭代。

```java
continue;
```

不同循环中，`continue` 的跳转位置略有区别：

- 在 `for` 循环中，`continue` 会跳到更新语句，然后再判断循环条件。
- 在 `while` 和 `do...while` 循环中，`continue` 会跳到布尔表达式判断。

示例：

```java
public class Test {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};

        for (int x : numbers) {
            if (x == 30) {
                continue;
            }

            System.out.print(x);
            System.out.print("\n");
        }
    }
}
```

输出：

```text
10
20
40
50
```

原因：

- 当 `x = 30` 时，执行 `continue`。
- `continue` 只跳过本轮循环中后续的输出语句。
- 循环并没有结束，因此后面的 `40` 和 `50` 仍会继续输出。

## break 与 continue 的区别

| 关键字 | 作用 | 对当前循环的影响 | 示例结果 |
| --- | --- | --- | --- |
| `break` | 结束整个循环 | 后续迭代都不再执行 | 遇到 `30` 后只输出 `10`、`20` |
| `continue` | 跳过本次迭代 | 后续迭代继续执行 | 跳过 `30`，输出 `10`、`20`、`40`、`50` |

简单记法：

- `break`：不循环了。
- `continue`：这轮算了，下一轮继续。

## 选择哪种循环

| 场景 | 推荐结构 | 原因 |
| --- | --- | --- |
| 条件满足才执行，次数不固定 | `while` | 先判断条件，再决定是否进入循环 |
| 至少执行一次，再看条件是否继续 | `do...while` | 循环体先执行 |
| 次数明确，或有标准初始化/条件/更新 | `for` | 结构集中，控制变量清晰 |
| 遍历数组或集合且不需要下标 | 增强 `for` | 写法简洁，不容易写错下标 |
| 满足某个条件后提前结束 | `break` | 直接跳出循环 |
| 某个元素或某次迭代不处理 | `continue` | 跳过本轮，保留后续迭代 |

## 容易踩的点

- `while` 和 `do...while` 中要确保循环条件会变化，否则可能死循环。
- `do...while` 的条件后面有分号：`} while (条件);`。
- `for` 的三个表达式都可以为空，但空条件容易形成无限循环。
- 增强 `for` 适合读取元素，不适合依赖下标进行复杂控制。
- `break` 结束循环，`continue` 只结束本轮迭代，这两个行为不要混淆。
- 多层循环中，普通 `break` 只跳出最里层循环。

## 小练习

1. 用 `while` 输出 `1` 到 `5`。
2. 用 `do...while` 验证“条件一开始为 false 时仍会执行一次”。
3. 用普通 `for` 输出数组下标和值。
4. 用增强 `for` 遍历字符串数组。
5. 在遍历 `{10, 20, 30, 40, 50}` 时，用 `break` 在遇到 `30` 时停止。
6. 在遍历 `{10, 20, 30, 40, 50}` 时，用 `continue` 跳过 `30`。
