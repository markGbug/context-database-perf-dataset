# 知识点 41991：Java：Java Scanner 类 - ScannerDemo.java 文件代码：

- 来源：[Java Scanner 类](https://www.runoob.com/java/java-scanner-class.html)
- 来源章节：[0901-java-scanner-class-study.md](../chapters/0901-java-scanner-class-study.md)
- 分类：后端开发
- 技术：Java
- 所在小节：ScannerDemo.java 文件代码：
- 知识类型：代码
- 原章节序号：0901

## 原文片段

```text
import java.util.Scanner;

public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据

        // next方式接收字符串
        System.out.println("next方式接收：");
        // 判断是否还有输入
        if (scan.hasNext()) {
            String str1 = scan.next();
            System.out.println("输入的数据为：" + str1);
        }
        scan.close();
    }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `ScannerDemo.java 文件代码：` 这一小节和 `Java Scanner 类` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
