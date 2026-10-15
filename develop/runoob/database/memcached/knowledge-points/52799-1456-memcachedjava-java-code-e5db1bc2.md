# 知识点 52799：Memcached：Java 连接 Memcached 服务 - MemcachedJava.java 文件：

- 来源：[Java 连接 Memcached 服务](https://www.runoob.com/memcached/java-memcached.html)
- 来源章节：[1456-java-memcached-practice.md](../chapters/1456-java-memcached-practice.md)
- 分类：数据库
- 技术：Memcached
- 所在小节：MemcachedJava.java 文件：
- 知识类型：代码
- 原章节序号：1456

## 原文片段

```text
import net.spy.memcached.MemcachedClient;
import java.net.*;


public class MemcachedJava {
   public static void main(String[] args) {
      try{
         // 本地连接 Memcached 服务
         MemcachedClient mcc = new MemcachedClient(new InetSocketAddress("127.0.0.1", 11211));
         System.out.println("Connection to server successful.");

         // 关闭连接
         mcc.shutdown();

      }catch(Exception ex){
         System.out.println( ex.getMessage() );
      }
   }
}
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `MemcachedJava.java 文件：` 这一小节和 `Java 连接 Memcached 服务` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
