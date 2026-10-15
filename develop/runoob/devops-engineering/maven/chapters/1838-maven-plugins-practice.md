# Maven：Maven 插件

- 来源：[Maven 插件](https://www.runoob.com/maven/maven-plugins.html)
- 分类：DevOps / 工程化
- 技术：Maven
- 笔记类型：练习笔记
- 章节序号：1838

## 本章内容

Maven 插件是扩展 Maven 功能的可执行组件，每个插件包含一个或多个目标(goals)，用于执行特定任务（如编译、测试、打包等）。

插件与生命周期的关系：

- 生命周期（Lifecycle）：定义构建阶段（phase）的顺序
- 插件（Plugin）：提供具体实现（goal）来完成这些阶段的任务

Maven 有以下三个标准的生命周期：

- clean：项目清理的处理
- default(或 build)：项目部署的处理
- site：项目站点文档创建的处理

每个生命周期中都包含着一系列的阶段(phase)。这些 phase 就相当于 Maven 提供的统一的接口，然后这些 phase 的实现由 Maven 的插件来完成。

我们在输入 mvn 命令的时候 比如 mvn clean，clean 对应的就是 Clean 生命周期中的 clean 阶段。但是 clean 的具体操作是由 maven-clean-plugin 来实现的。

所以说 Maven 生命周期的每一个阶段的具体实现都是由 Maven 插件实现的。

Maven 实际上是一个依赖插件执行的框架，每个任务实际上是由插件完成。Maven 插件通常被用来：

- 创建 jar 文件
- 创建 war 文件
- 编译代码文件
- 代码单元测试
- 创建工程文档
- 创建工程报告


## 插件核心机制


### 插件坐标

与依赖类似，插件也通过 groupId、artifactId、version 唯一标识：


### 插件目标（Goals）

每个插件可以包含多个目标，例如：

- maven-compiler-plugin：compile：编译主代码testCompile：编译测试代码
- maven-surefire-plugin：test：运行单元测试


### 插件绑定方式

Maven 已为生命周期阶段预绑定插件目标：

在 pom.xml 中显式配置：

```html
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
            <executions>
                <execution>
                    <phase>compile</phase>  <!-- 绑定到 compile 阶段 -->
                    <goals>
                        <goal>compile</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```


## 常用官方插件


### 编译相关

配置示例：

```html
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.8.1</version>
    <configuration>
        <source>11</source>  <!-- Java 版本 -->
        <target>11</target>
    </configuration>
</plugin>
```


### 测试相关

跳过测试配置：

```html
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.2</version>
    <configuration>
        <skipTests>true</skipTests>  <!-- 跳过测试 -->
    </configuration>
</plugin>
```


### 打包相关

可执行 JAR 配置：

```html
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-jar-plugin</artifactId>
    <version>3.2.0</version>
    <configuration>
        <archive>
            <manifest>
                <mainClass>com.example.Main</mainClass>  <!-- 指定主类 -->
            </manifest>
        </archive>
    </configuration>
</plugin>
```


### 部署相关


## 插件调用方式

通过生命周期调用:

```text
mvn compile  # 触发 maven-compiler-plugin:compile
```

直接调用插件目标:

```text
mvn compiler:compile  # 直接调用编译目标
```

命令行参数配置:

```text
mvn compiler:compile -Dmaven.compiler.source=11
```


## 自定义插件配置


### 参数配置

通过 configuration 标签设置：

```html
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <version>2.22.2</version>
    <configuration>
        <includes>
            <include>**/*Test.java</include>  <!-- 只包含特定测试 -->
        </includes>
    </configuration>
</plugin>
```

多目标执行:

```html
<executions>
    <execution>
        <id>run-tests</id>
        <phase>test</phase>
        <goals>
            <goal>test</goal>
        </goals>
    </execution>
</executions>
```


## 插件开发基础


### Mojo 概念

- 插件目标对应的 Java 类称为 Mojo（Maven plain Old Java Object）。
- 必须继承 AbstractMojo 并实现 execute() 方法。


### 简单插件示例


## 实例


### 打包和安装插件

```text
mvn clean install  # 将插件安装到本地仓库
```


## 插件类型

Maven 提供了下面两种类型的插件：

下面是一些常用插件的列表：


### 实例

我们已经在我们的例子中大量使用了 maven-antrun-plugin 来输出数据到控制台上。请查看 Maven - 构建配置文件 章节。让我们用一种更好的方式理解这部分内容，在 C:\MVN\project 目录下创建一个 pom.xml 文件。

```html
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
<groupId>com.companyname.projectgroup</groupId>
<artifactId>project</artifactId>
<version>1.0</version>
<build>
<plugins>
   <plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-antrun-plugin</artifactId>
   <version>1.1</version>
   <executions>
      <execution>
         <id>id.clean</id>
         <phase>clean</phase>
         <goals>
            <goal>run</goal>
         </goals>
         <configuration>
            <tasks>
               <echo>clean phase</echo>
            </tasks>
         </configuration>
      </execution>
   </executions>
   </plugin>
</plugins>
</build>
</project>
```

接下来，打开命令终端跳转到 pom.xml 所在的目录，并执行下面的 mvn 命令。

```text
mvn clean
```

Maven 将开始处理并显示 clean 生命周期的 clean 阶段。

```text
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------
[INFO] Building Unnamed - com.companyname.projectgroup:project:jar:1.0
[INFO]    task-segment: [post-clean]
[INFO] ------------------------------------------------------------------
[INFO] [clean:clean {execution: default-clean}]
[INFO] [antrun:run {execution: id.clean}]
[INFO] Executing tasks
     [echo] clean phase
[INFO] Executed tasks
[INFO] ------------------------------------------------------------------
[INFO] BUILD SUCCESSFUL
[INFO] ------------------------------------------------------------------
[INFO] Total time: < 1 second
[INFO] Finished at: Sat Jul 07 13:38:59 IST 2012
[INFO] Final Memory: 4M/44M
[INFO] ------------------------------------------------------------------
```

上面的例子展示了以下关键概念：

- 插件是在 pom.xml 中使用 plugins 元素定义的。
- 每个插件可以有多个目标。
- 你可以定义阶段，插件会使用它的 phase 元素开始处理。我们已经使用了 clean 阶段。
- 你可以通过绑定到插件的目标的方式来配置要执行的任务。我们已经绑定了 echo 任务到 maven-antrun-plugin 的 run 目标。
- 就是这样，Maven 将处理剩下的事情。它将下载本地仓库中获取不到的插件，并开始处理。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Maven 插件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
