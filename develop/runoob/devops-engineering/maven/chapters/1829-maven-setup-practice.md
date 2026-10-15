# Maven：Maven 环境配置

- 来源：[Maven 环境配置](https://www.runoob.com/maven/maven-setup.html)
- 分类：DevOps / 工程化
- 技术：Maven
- 笔记类型：练习笔记
- 章节序号：1829

## 本章内容

Maven 是一个基于 Java 的工具，所以要做的第一件事情就是安装 JDK。

下载 JDK（推荐 JDK 8/11/17）：

- Oracle JDK
- OpenJDK

如果你还未安装 JDK，可以参考我们的 Java 开发环境配置。


### 系统要求


### 检查 Java 安装

```text
c:\> java -version
```

```text
# java -version
```

```text
$ java -version
```


### Maven 下载

Maven 下载地址：http://maven.apache.org/download.cgi

不同平台下载对应的包：

下载包后解压到对应目录：


### 设置 Maven 环境变量

添加环境变量 MAVEN_HOME：

右键 "计算机"，选择 "属性"，之后点击 "高级系统设置"，点击"环境变量"，来设置环境变量，有以下系统变量需要配置：

新建系统变量 MAVEN_HOME，变量值：E:\Maven\apache-maven-3.3.9

编辑系统变量 Path，添加变量值：;%MAVEN_HOME%\bin

注意：注意多个值之间需要有分号隔开，然后点击确定。

下载解压：

```text
# wget http://mirrors.hust.edu.cn/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
# tar -xvf  apache-maven-3.3.9-bin.tar.gz
# sudo mv -f apache-maven-3.3.9 /usr/local/
```

编辑 /etc/profile 文件 sudo vim /etc/profile，在文件末尾添加如下代码：

```text
export MAVEN_HOME=/usr/local/apache-maven-3.3.9
export PATH=${PATH}:${MAVEN_HOME}/bin
```

保存文件，并运行如下命令使环境变量生效：

```text
# source /etc/profile
```

在控制台输入如下命令，如果能看到 Maven 相关版本信息，则说明 Maven 已经安装成功：

```text
# mvn -v
```

下载解压：

```text
$ curl -O http://mirrors.hust.edu.cn/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
$ tar -xvf  apache-maven-3.3.9-bin.tar.gz
$ sudo mv -f apache-maven-3.3.9 /usr/local/
```

编辑 /etc/profile 文件 sudo vim /etc/profile，在文件末尾添加如下代码：

```text
export MAVEN_HOME=/usr/local/apache-maven-3.3.9
export PATH=${PATH}:${MAVEN_HOME}/bin
```

保存文件，并运行如下命令使环境变量生效：

```text
$ source /etc/profile
```

在控制台输入如下命令，如果能看到 Maven 相关版本信息，则说明 Maven 已经安装成功：

```text
$ mvn -v
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-11T00:41:47+08:00)
Maven home: /usr/local/apache-maven-3.3.9
Java version: 1.8.0_31, vendor: Oracle Corporation
Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_31.jdk/Contents/Home/jre
Default locale: zh_CN, platform encoding: ISO8859-1
OS name: "mac os x", version: "10.13.4", arch: "x86_64", family: "mac"
```


### 验证安装

```text
mvn -v  # 应输出 Maven 版本和 Java 信息
```


### 配置 Maven 本地仓库

Maven 默认从远程仓库下载依赖，并存储在本地：

默认本地仓库路径：

- Windows: C:\Users\<用户名>\.m2\repository
- Linux/macOS: ~/.m2/repository

修改仓库位置（可选）：

在 MAVEN_HOME/conf/settings.xml 中修改：

```html
<localRepository>/path/to/your/repo</localRepository>
```


## 第一个 Maven 项目


### 使用 Maven 创建项目

运行以下命令生成标准 Java 项目：

```text
mvn archetype:generate \
    -DgroupId=com.example \
    -DartifactId=my-first-app \
    -DarchetypeArtifactId=maven-archetype-quickstart \
    -DinteractiveMode=false
```

这会生成一个标准 Maven 项目结构：

```text
my-first-app/
├── pom.xml           # 项目配置文件
├── src/
│   ├── main/         # 主代码
│   │   └── java/     # Java 源代码
│   └── test/         # 测试代码
│       └── java/     # 测试类
```


### 解读 pom.xml

生成的 pom.xml 示例：

```html
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>      <!-- 组织名 -->
    <artifactId>my-first-app</artifactId>  <!-- 项目名 -->
    <version>1.0-SNAPSHOT</version>     <!-- 版本号 -->

    <dependencies>
        <dependency>
            <groupId>junit</groupId>    <!-- 测试依赖 -->
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>         <!-- 仅用于测试 -->
        </dependency>
    </dependencies>
</project>
```


### 编译和运行

```text
mvn compile    # 编译项目
mvn test       # 运行测试
mvn package    # 打包成 .jar 文件
java -jar target/my-first-app-1.0-SNAPSHOT.jar  # 运行（如果可执行）
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Maven 环境配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
