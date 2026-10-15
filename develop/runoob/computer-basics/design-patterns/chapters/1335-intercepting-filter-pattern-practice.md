# 设计模式：拦截过滤器模式

- 来源：[拦截过滤器模式](https://www.runoob.com/design-pattern/intercepting-filter-pattern.html)
- 分类：计算机基础
- 技术：设计模式
- 笔记类型：练习笔记
- 章节序号：1335

## 本章内容

拦截过滤器模式（Intercepting Filter Pattern）用于对应用程序的请求或响应做一些预处理/后处理。定义过滤器，并在把请求传给实际目标应用程序之前应用在请求上。过滤器可以做认证/授权/记录日志，或者跟踪请求，然后把请求传给相应的处理程序。以下是这种设计模式的实体。

- 过滤器（Filter） - 过滤器在请求处理程序执行请求之前或之后，执行某些任务。
- 过滤器链（Filter Chain） - 过滤器链带有多个过滤器，并在 Target 上按照定义的顺序执行这些过滤器。
- Target - Target 对象是请求处理程序。
- 过滤管理器（Filter Manager） - 过滤管理器管理过滤器和过滤器链。
- 客户端（Client） - Client 是向 Target 对象发送请求的对象。


## 概要


### 意图

用于在请求到达最终目的地之前，通过一系列过滤器对请求进行预处理和后处理。


### 主要解决的问题

- 解决Web应用程序中需要在请求处理前后执行通用操作（如日志记录、安全检查、事务管理等）的问题。


### 使用场景

- 当需要在请求处理流程中插入额外的逻辑，而这些逻辑与业务逻辑无关时。


### 实现方式

- 过滤器链：一系列过滤器按照特定顺序执行。
- 过滤器：对请求和响应进行预处理和后处理的组件。
- 目标对象：请求处理的最终目的地。


### 关键代码

- 过滤器接口：定义了过滤器必须实现的方法，如before()和after()。
- 具体过滤器：实现过滤器接口，包含具体的处理逻辑。
- 过滤器管理器：负责过滤器链的维护和过滤器的调用顺序。


### 应用实例

- Web应用服务器：如Tomcat使用过滤器进行请求的拦截处理，例如权限检查、日志记录等。


### 优点

- 职责分离：将通用操作与业务逻辑分离，提高代码的可维护性。
- 可扩展性：可以灵活地添加、删除或修改过滤器。
- 复用性：过滤器可以在不同的请求处理中重用。


### 缺点

- 性能影响：如果过滤器链过长或过滤器执行的操作复杂，可能会影响性能。


### 使用建议

- 当需要在请求处理流程中插入与业务逻辑无关的通用操作时，考虑使用拦截过滤器模式。


### 注意事项

- 确保过滤器的执行顺序符合预期，以避免逻辑错误。


### 包含的几个主要角色

- 过滤器接口（Filter Interface）： 定义了过滤器必须实现的方法。
- 具体过滤器（Concrete Filter）： 实现过滤器接口，包含具体的处理逻辑。
- 过滤器管理器（Filter Manager）： 负责维护过滤器链和调用过滤器。
- 目标对象（Target）： 请求处理的最终目的地，业务逻辑的实现。
- 客户端（Client）（可选）： 发出请求的Web浏览器或API客户端。

拦截过滤器模式通过在请求处理流程中插入通用操作，有助于保持业务逻辑的清晰和专注。


## 实现

我们将创建 FilterChain、FilterManager、Target、Client 作为表示实体的各种对象。AuthenticationFilter 和 DebugFilter 表示实体过滤器。

InterceptingFilterDemo 类使用 Client 来演示拦截过滤器设计模式。


## 步骤 1

创建过滤器接口 Filter。


## Filter.java

```text
public interface Filter {
   public void execute(String request);
}
```


## 步骤 2

创建实体过滤器。


## AuthenticationFilter.java

```java
public class AuthenticationFilter implements Filter {
   public void execute(String request){
      System.out.println("Authenticating request: " + request);
   }
}
```


## DebugFilter.java

```java
public class DebugFilter implements Filter {
   public void execute(String request){
      System.out.println("request log: " + request);
   }
}
```


## 步骤 3

创建 Target。


## Target.java

```java
public class Target {
   public void execute(String request){
      System.out.println("Executing request: " + request);
   }
}
```


## 步骤 4

创建过滤器链。


## FilterChain.java

```java
import java.util.ArrayList;
import java.util.List;

public class FilterChain {
   private List<Filter> filters = new ArrayList<Filter>();
   private Target target;

   public void addFilter(Filter filter){
      filters.add(filter);
   }

   public void execute(String request){
      for (Filter filter : filters) {
         filter.execute(request);
      }
      target.execute(request);
   }

   public void setTarget(Target target){
      this.target = target;
   }
}
```


## 步骤 5

创建过滤管理器。


## FilterManager.java

```java
public class FilterManager {
   FilterChain filterChain;

   public FilterManager(Target target){
      filterChain = new FilterChain();
      filterChain.setTarget(target);
   }
   public void setFilter(Filter filter){
      filterChain.addFilter(filter);
   }

   public void filterRequest(String request){
      filterChain.execute(request);
   }
}
```


## 后续章节

- 步骤 6
- Client.java
- 步骤 7
- InterceptingFilterDemo.java
- 步骤 8

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `拦截过滤器模式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
