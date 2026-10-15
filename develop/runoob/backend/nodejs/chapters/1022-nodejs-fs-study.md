# Node.js：Node.js 文件系统

- 来源：[Node.js 文件系统](https://www.runoob.com/nodejs/nodejs-fs.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1022

## 本章内容

Node.js 的文件系统模块（fs 模块）提供了丰富的 API，用于读取、写入、删除文件以及执行其他文件系统操作。

fs 模块既支持同步方法也支持异步方法，使得开发者可以根据具体需求选择合适的方式来处理文件操作。


### 导入 fs 模块

首先，你需要导入 fs 模块：

```javascript
var fs = require("fs")
```


## 异步和同步

Node.js 文件系统（fs 模块）模块中的方法均有异步和同步版本，例如读取文件内容的函数有异步的 fs.readFile() 和同步的 fs.readFileSync()。

异步的方法函数最后一个参数为回调函数，回调函数的第一个参数包含了错误信息(error)。

建议大家使用异步方法，比起同步，异步方法性能更高，速度更快，而且没有阻塞。


### 实例

创建 example.txt 文件，内容如下：

```text
菜鸟教程官网地址：www.runoob.com
文件读取实例
```

创建 file.js 文件, 代码如下：


## 实例

以上代码执行结果如下：

```text
$ node file.js
同步读取: 菜鸟教程官网地址：www.runoob.com
文件读取实例

程序执行完毕。
异步读取: 菜鸟教程官网地址：www.runoob.com
文件读取实例
```


### 写入文件

异步写入文件:

```javascript
fs.writeFile('example.txt', 'Hello, World!', (err) => {
    if (err) {
        console.error('Error writing file:', err);
        return;
    }
    console.log('File written successfully');
});
```

同步写入文件:

```javascript
try {
    fs.writeFileSync('example.txt', 'Hello, World!');
    console.log('File written successfully');
} catch (err) {
    console.error('Error writing file:', err);
}
```


### 附加内容到文件

异步附加内容:

```javascript
fs.appendFile('example.txt', '\nAppending some text', (err) => {
    if (err) {
        console.error('Error appending to file:', err);
        return;
    }
    console.log('Text appended successfully');
});
```

同步附加内容:

```javascript
try {
    fs.appendFileSync('example.txt', '\nAppending some text');
    console.log('Text appended successfully');
} catch (err) {
    console.error('Error appending to file:', err);
}
```


### 删除文件

异步删除文件:

```javascript
fs.unlink('example.txt', (err) => {
    if (err) {
        console.error('Error deleting file:', err);
        return;
    }
    console.log('File deleted successfully');
});
```

同步删除文件:

```javascript
try {
    fs.unlinkSync('example.txt');
    console.log('File deleted successfully');
} catch (err) {
    console.error('Error deleting file:', err);
}
```


### 创建目录

异步创建目录:

```javascript
fs.mkdir('new_directory', (err) => {
    if (err) {
        console.error('Error creating directory:', err);
        return;
    }
    console.log('Directory created successfully');
});
```

同步创建目录:

```javascript
try {
    fs.mkdirSync('new_directory');
    console.log('Directory created successfully');
} catch (err) {
    console.error('Error creating directory:', err);
}
```


### 读取目录内容

异步读取目录内容:

```javascript
fs.readdir('new_directory', (err, files) => {
    if (err) {
        console.error('Error reading directory:', err);
        return;
    }
    console.log('Directory contents:', files);
});
```

同步读取目录内容:

```javascript
try {
    const files = fs.readdirSync('new_directory');
    console.log('Directory contents:', files);
} catch (err) {
    console.error('Error reading directory:', err);
}
```


### 检查文件或目录是否存在

异步检查:

```javascript
fs.access('example.txt', fs.constants.F_OK, (err) => {
    if (err) {
        console.log('File does not exist');
    } else {
        console.log('File exists');
    }
});
```

同步检查:

```javascript
try {
    fs.accessSync('example.txt', fs.constants.F_OK);
    console.log('File exists');
} catch (err) {
    console.log('File does not exist');
}
```


### 高级用法

1、文件流

文件流可以用于高效地读取和写入大文件，而不会一次性将整个文件加载到内存中。

读取文件流：

```javascript
const fs = require('fs');

const readableStream = fs.createReadStream('large_file.txt', 'utf8');

readableStream.on('data', (chunk) => {
    console.log('Received chunk:', chunk);
});

readableStream.on('end', () => {
    console.log('No more data.');
});
```

写入文件流：

```javascript
const fs = require('fs');

const writableStream = fs.createWriteStream('output.txt');

writableStream.write('Hello, ');
writableStream.write('World!\n');

writableStream.end();

writableStream.on('finish', () => {
    console.log('All writes are now complete.');
});
```

2、文件系统统计信息

可以使用 fs.stat 或 fs.lstat 获取文件或目录的统计信息。

异步获取统计信息：

```javascript
fs.stat('example.txt', (err, stats) => {
    if (err) {
        console.error('Error getting stats:', err);
        return;
    }
    console.log('Is file?', stats.isFile());
    console.log('Is directory?', stats.isDirectory());
    console.log('Size:', stats.size);
});
```

同步获取统计信息：

```javascript
try {
    const stats = fs.statSync('example.txt');
    console.log('Is file?', stats.isFile());
    console.log('Is directory?', stats.isDirectory());
    console.log('Size:', stats.size);
} catch (err) {
    console.error('Error getting stats:', err);
}
```

接下来，让我们来具体了解下 Node.js 文件系统的方法。


## 打开文件


### 语法

以下为在异步模式下打开文件的语法格式：

```text
fs.open(path, flags[, mode], callback)
```


### 参数

参数使用说明如下：

- path - 文件的路径。
- flags - 文件打开的行为。具体值详见下文。
- mode - 设置文件模式(权限)，文件创建默认权限为 0666(可读，可写)。
- callback - 回调函数，带有两个参数如：callback(err, fd)。

flags 参数可以是以下值：


### 实例

接下来我们创建 file.js 文件，并打开 input.txt 文件进行读写，代码如下所示：

```javascript
var fs = require("fs");

// 异步打开文件
console.log("准备打开文件！");
fs.open('input.txt', 'r+', function(err, fd) {
   if (err) {
       return console.error(err);
   }
  console.log("文件打开成功！");
});
```

以上代码执行结果如下：

```text
$ node file.js
准备打开文件！
文件打开成功！
```


## 获取文件信息


### 语法

以下为通过异步模式获取文件信息的语法格式：

```text
fs.stat(path, callback)
```


### 参数

参数使用说明如下：

- path - 文件路径。
- callback - 回调函数，带有两个参数如：(err, stats), stats 是 fs.Stats 对象。

fs.stat(path)执行后，会将stats类的实例返回给其回调函数。可以通过stats类中的提供方法判断文件的相关属性。例如判断是否为文件：

```javascript
var fs = require('fs');

fs.stat('/Users/liuht/code/itbilu/demo/fs.js', function (err, stats) {
    console.log(stats.isFile());         //true
})
```

stats类中的方法有：


### 实例

接下来我们创建 file.js 文件，代码如下所示：

```javascript
var fs = require("fs");

console.log("准备打开文件！");
fs.stat('input.txt', function (err, stats) {
   if (err) {
       return console.error(err);
   }
   console.log(stats);
   console.log("读取文件信息成功！");

   // 检测文件类型
   console.log("是否为文件(isFile) ? " + stats.isFile());
   console.log("是否为目录(isDirectory) ? " + stats.isDirectory());
});
```

以上代码执行结果如下：

```text
$ node file.js
准备打开文件！
{ dev: 16777220,
  mode: 33188,
  nlink: 1,
  uid: 501,
  gid: 20,
  rdev: 0,
  blksize: 4096,
  ino: 40333161,
  size: 61,
  blocks: 8,
  atime: Mon Sep 07 2015 17:43:55 GMT+0800 (CST),
  mtime: Mon Sep 07 2015 17:22:35 GMT+0800 (CST),
  ctime: Mon Sep 07 2015 17:22:35 GMT+0800 (CST) }
读取文件信息成功！
是否为文件(isFile) ? true
是否为目录(isDirectory) ? false
```


## 写入文件


### 语法

以下为异步模式下写入文件的语法格式：

```text
fs.writeFile(file, data[, options], callback)
```

writeFile 直接打开文件默认是 w 模式，所以如果文件存在，该方法写入的内容会覆盖旧的文件内容。


### 参数

参数使用说明如下：

- file - 文件名或文件描述符。
- data - 要写入文件的数据，可以是 String(字符串) 或 Buffer(缓冲) 对象。
- options - 该参数是一个对象，包含 {encoding, mode, flag}。默认编码为 utf8, 模式为 0666 ， flag 为 'w'
- callback - 回调函数，回调函数只包含错误信息参数(err)，在写入失败时返回。


### 实例

接下来我们创建 file.js 文件，代码如下所示：

```javascript
var fs = require("fs");

console.log("准备写入文件");
fs.writeFile('input.txt', '我是通 过fs.writeFile 写入文件的内容',  function(err) {
   if (err) {
       return console.error(err);
   }
   console.log("数据写入成功！");
   console.log("--------我是分割线-------------")
   console.log("读取写入的数据！");
   fs.readFile('input.txt', function (err, data) {
      if (err) {
         return console.error(err);
      }
      console.log("异步读取文件数据: " + data.toString());
   });
});
```

以上代码执行结果如下：

```text
$ node file.js
准备写入文件
数据写入成功！
--------我是分割线-------------
读取写入的数据！
异步读取文件数据: 我是通 过fs.writeFile 写入文件的内容
```


## 读取文件


## 后续章节

- 语法
- 参数
- 实例
- 关闭文件
- 语法
- 参数
- 实例
- 截取文件
- 语法
- 参数
- 实例
- 删除文件
- 语法
- 参数
- 实例
- 创建目录

## 复习重点

- 能说明 `Node.js 文件系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
