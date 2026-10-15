# Maven：Maven 第一个项目

- 来源：[Maven 第一个项目](https://www.runoob.com/maven/maven-start.html)
- 分类：DevOps / 工程化
- 技术：Maven
- 笔记类型：学习笔记
- 章节序号：1830

## 本章内容

## 创建 Maven 项目

### 使用 Maven Archetype 生成项目

Maven 提供了项目模板（Archetype），可以快速生成标准项目结构。最常用的是 maven-archetype-quickstart（基础 Java 项目模板）。

执行命令：

```text
mvn archetype:generate \
    -DgroupId=com.example \
    -DartifactId=my-first-app \
    -DarchetypeArtifactId=maven-archetype-quickstart \
    -DinteractiveMode=false
```

参数说明：

执行后生成的项目结构：

```text
my-first-app/
├── pom.xml           # Maven 项目配置文件
├── src/
│   ├── main/         # 主代码目录
│   │   └── java/     # Java 源代码
│   │       └── com/example/App.java  # 自动生成的示例类
│   └── test/        # 测试代码目录
│       └── java/     # 测试类
│           └── com/example/AppTest.java  # 自动生成的测试类
```

## 项目结构解析

### pom.xml 详解

这是 Maven 的核心配置文件，定义了项目的基本信息和依赖。

生成的 pom.xml 示例：

```html
<project>
    <!-- POM 模型版本，固定 4.0.0 -->
    <modelVersion>4.0.0</modelVersion>

    <!-- 项目坐标（唯一标识） -->
    <groupId>com.example</groupId>
    <artifactId>my-first-app</artifactId>
    <version>1.0-SNAPSHOT</version>

    <!-- 项目打包方式（默认 jar，也可以是 war、pom 等） -->
    <packaging>jar</packaging>

    <!-- 项目名称和 URL（可选） -->
    <name>my-first-app</name>
    <url>http://www.example.com</url>

    <!-- 依赖管理 -->
    <dependencies>
        <!-- JUnit 测试依赖 -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>  <!-- 仅用于测试 -->
        </dependency>
    </dependencies>
</project>
```

### 源代码结构

### 示例代码：

主类 App.java

## 实例

测试类 AppTest.java:

## 实例

## 构建与运行

### 常用 Maven 命令

### 完整构建流程

1、编译项目：

```text
mvn compile
```

编译后的 .class 文件会放在 target/classes 目录。

2、运行测试：

```text
mvn test
```

执行 src/test/java 下的测试类。

3、打包：

```text
mvn package
```

生成 target/my-first-app-1.0-SNAPSHOT.jar。

4、运行程序：

```text
java -cp target/my-first-app-1.0-SNAPSHOT.jar com.example.App
```

5、输出：

```text
Hello Maven!
```

## 扩展：修改项目

### 添加依赖

例如，添加 Gson 用于 JSON 处理：

修改 pom.xml：

```html
<dependencies>
    <!-- 原有 JUnit 依赖 -->
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>

    <!-- 新增 Gson 依赖 -->
    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.8.9</version>
    </dependency>
</dependencies>
```

运行 mvn compile，Maven 会自动下载 Gson。

### 修改主类使用 Gson

## 实例

重新打包并运行：

```text
mvn package
java -cp target/my-first-app-1.0-SNAPSHOT.jar com.example.App
```

输出：

```text
"Hello Maven with Gson!"
```

## 常见问题

### 依赖下载失败

原因：网络问题或仓库不可用。

解决方案：

检查网络连接。

配置国内镜像仓库（如阿里云）：

```html
<!-- 在 settings.xml 或 pom.xml 中配置 -->
<mirror>
    <id>aliyun</id>
    <url>https://maven.aliyun.com/repository/public</url>
    <mirrorOf>central</mirrorOf>
</mirror>
```

阿里云仓库介绍：https://developer.aliyun.com/mvn/guide。

### 编译版本问题

错误：javac: invalid target release: 11

解决方案：在 pom.xml 中指定 Java 版本：

```html
<properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
</properties>
```

## 总结

创建项目：mvn archetype:generate 生成标准结构。

项目结构：

pom.xml 定义依赖和配置。

src/main/java 放主代码，src/test/java 放测试代码。

构建命令：

mvn compile → mvn test → mvn package。

运行：java -jar 或 java -cp 执行 .jar 文件。

## 复习重点

- 能解释 `Maven 第一个项目` 的用途和关键步骤。
- 能根据示例推导输出或执行结果。
- 能指出一个容易踩坑的地方。
