# Ruby：Ruby 安装 - Linux

- 来源：[Ruby 安装 - Linux](https://www.runoob.com/ruby/ruby-installation-unix.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3712

## 本章内容

下面列出了在 Linux 机器上安装 Ruby 的步骤。

注意：在安装之前，请确保您有 root 权限。


## 源码安装

- 下载最新版的 Ruby 压缩文件。请点击这里下载。
- 下载 Ruby 之后，解压到新创建的目录下：

```text
$ tar -xvzf ruby-2.2.3.tgz
$ cd ruby-2.2.3
```

- 现在，配置并编译源代码，如下所示：

```text
$ ./configure
$ make
$ sudo make install
```

- 安装后，通过在命令行中输入以下命令来确保一切工作正常：

```text
$ruby -v
ruby 2.2.3……
```

- 如果一切工作正常，将会输出所安装的 Ruby 解释器的版本，如上所示。如果您安装了其他版本，则会显示其他不同的版本。


## 自动安装 Ruby

如果您的计算机已经连接到 Internet，那么最简单安装 Ruby 的方式是使用 yum 或 apt-get。在命令提示符中输入以下的命令，即可在您的计算机上安装 Ruby。

```text
$  sudo yum install ruby    # CentOS, Fedora, 或 RHEL 系统

或

sudo apt-get install ruby-full # Debian 或 Ubuntu 系统
```

如果你是苹果系统，可以使用 brew 命令安装：

```text
$ brew install ruby
```


## 使用 RVM 安装 Ruby

RVM 能在系统中安装和管理多个 Ruby 版本。同时还能管理不同的 gem 集。支持 OS X、Linux 和其它类 UNIX 操作系统。


### 安装 RVM

```text
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
$ curl -sSL https://get.rvm.io | bash -s stable
```

安装完成后，会列出一些安装信息，其中有一行要注意：

```text
...
To start using RVM you need to run `source /etc/profile.d/rvm.sh`
....
```

意思是如果要开始使用需要执行一个 source 命令来重新执行刚修改的初始化文件，根据安装提示，执行以下命令载入 RVM 环境（新开 Termal 就不用这么做了，会自动重新载入的）

```text
source /etc/profile.d/rvm.sh
```

检查一下是否安装正确

```html
$ rvm -v
rvm 1.22.17 (stable) by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.io/]
```


### 用 RVM 安装 Ruby 环境

列出已知的 ruby 版本:

```text
$ rvm list known
```

可以选择现有的 rvm 版本来进行安装（下面以 rvm 2.4.2 版本的安装为例）

```text
$ rvm install 2.4.2
```

同样继续等待漫长的下载，编译过程，完成以后，Ruby, Ruby Gems 就安装好了。


### rvm 常用命令

查询已经安装的 ruby

```text
$ rvm list
```

卸载一个已安装版本

```text
$ rvm remove 1.9.2
```

设置 Ruby 版本

RVM 装好以后，需要执行下面的命令将指定版本的 Ruby 设置为系统默认版本

```text
$ rvm 2.0.0 --default
```

同样，也可以用其他版本号，前提是你有用 rvm install 安装过那个版本

这个时候你可以测试是否正确

```text
$ ruby -v
ruby 2.0.0p247 (2013-06-27 revision 41674) [x86_64-darwin13.0.0]

$ gem -v
2.1.6
```

这有可能是因为 Ruby 的默认源使用的是 cocoapods.org，国内访问这个网址有时候会有问题，网上的一种解决方案是将远替换成 ruby-china 的，替换方式如下：

```text
$ gem source -r https://rubygems.org/
$ gem source -a https://gems.ruby-china.com/
```

要想验证是否替换成功了，可以执行：

```text
$ gem sources -l
```

正常的输出结果：

```text
*** CURRENT SOURCES ***

https://gems.ruby-china.com/
```

请确保只有 gems.ruby-china.com

```text
$ gem install rails
```

如果你使用 Gemfile 和 Bundle (例如：Rails 项目)

你可以用 Bundler 的 Gem 源代码镜像命令。

```text
$ bundle config mirror.https://rubygems.org https://gems.ruby-china.com
```

这样你不用改你的 Gemfile 的 source。

```text
source 'https://rubygems.org/'
gem 'rails', '4.1.0'
...
```


## 复习重点

- 能说明 `Ruby 安装 - Linux` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
