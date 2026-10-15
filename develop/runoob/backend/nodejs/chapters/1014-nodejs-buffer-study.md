# Node.js：Node.js Buffer(缓冲区)

- 来源：[Node.js Buffer](https://www.runoob.com/nodejs/nodejs-buffer.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1014

## 本章内容

JavaScript 语言自身只有字符串数据类型，没有二进制数据类型。

Node.js 中的 Buffer 类是用于处理二进制数据的核心工具，提供了对二进制数据的高效操作。

Buffer 类在处理文件操作、网络通信、图像处理等场景中特别有用。

特性：

- 二进制数据：Buffer 对象是一个包含原始二进制数据的固定大小的数组。每个元素占用一个字节（8位），因此 Buffer 适合处理二进制数据，如文件内容、网络数据包等。
- 不可变性：虽然 Buffer 对象的内容可以在创建后修改，但其长度是固定的，不能动态改变。


## Buffer 与字符编码

Buffer 实例一般用于表示编码字符的序列，比如 UTF-8 、 UCS2 、 Base64 、或十六进制编码的数据。 通过使用显式的字符编码，就可以在 Buffer 实例与普通的 JavaScript 字符串之间进行相互转换。


## 实例

Node.js 目前支持的字符编码包括：

- ascii - 仅支持 7 位 ASCII 数据。如果设置去掉高位的话，这种编码是非常快的。
- utf8 - 多字节编码的 Unicode 字符。许多网页和其他文档格式都使用 UTF-8 。
- utf16le - 2 或 4 个字节，小字节序编码的 Unicode 字符。支持代理对（U+10000 至 U+10FFFF）。
- ucs2 - utf16le 的别名。
- base64 - Base64 编码。
- latin1 - 一种把 Buffer 编码成一字节编码的字符串的方式。
- binary - latin1 的别名。
- hex - 将每个字节编码为两个十六进制字符。


## 创建 Buffer 类

Buffer 提供了以下 API 来创建 Buffer 类：

- Buffer.alloc(size[, fill[, encoding]])： 创建了一个长度为 size 字节的 Buffer，相当于申请了 size 字节的内存空间，每个字节的值为 0。
- Buffer.allocUnsafe(size)： 建了一个长度为 size 字节的 Buffer，但 Buffer 中可能存在旧的数据，可能会影响执行结果，所以叫 unsafe。
- Buffer.allocUnsafeSlow(size)：用于分配给定大小 size 的新 Buffer 实例，但不对其进行初始化。
- Buffer.from(array)： 返回一个被 array 的值初始化的新的 Buffer 实例（传入的 array 的元素只能是数字，不然就会自动被 0 覆盖）
- Buffer.from(arrayBuffer[, byteOffset[, length]])： 返回一个新建的与给定的 ArrayBuffer 共享同一内存的 Buffer。
- Buffer.from(buffer)： 复制传入的 Buffer 实例的数据，并返回一个新的 Buffer 实例
- Buffer.from(string[, encoding])： 通过字符串创建 Buffer，可以指定编码，默认为 UTF-8。


## 实例


## 写入缓冲区


### 语法

写入 Node 缓冲区的语法如下所示：

```text
buf.write(string[, offset[, length]][, encoding])
```


### 参数

参数描述如下：

- string - 写入缓冲区的字符串。
- offset - 缓冲区开始写入的索引值，默认为 0 。
- length - 写入的字节数，默认为 buffer.length
- encoding - 使用的编码。默认为 'utf8' 。

根据 encoding 的字符编码写入 string 到 buf 中的 offset 位置。 length 参数是写入的字节数。 如果 buf 没有足够的空间保存整个字符串，则只会写入 string 的一部分。 只部分解码的字符不会被写入。


### 返回值

返回实际写入的大小。如果 buffer 空间不足， 则只会写入部分字符串。


### 实例

```javascript
buf = Buffer.alloc(256);
len = buf.write("www.runoob.com");

console.log("写入字节数 : "+  len);
```

执行以上代码，输出结果为：

```text
$node main.js
写入字节数 : 14
```


## 从缓冲区读取数据


### 语法

读取 Node 缓冲区数据的语法如下所示：

```text
buf.toString([encoding[, start[, end]]])
```


### 参数

参数描述如下：

- encoding - 使用的编码。默认为 'utf8' 。
- start - 指定开始读取的索引位置，默认为 0。
- end - 结束位置，默认为缓冲区的末尾。


### 返回值

解码缓冲区数据并使用指定的编码返回字符串。


### 实例

```java
buf = Buffer.alloc(26);
for (var i = 0 ; i < 26 ; i++) {
  buf[i] = i + 97;
}

console.log( buf.toString('ascii'));       // 输出: abcdefghijklmnopqrstuvwxyz
console.log( buf.toString('ascii',0,5));   //使用 'ascii' 编码, 并输出: abcde
console.log( buf.toString('utf8',0,5));    // 使用 'utf8' 编码, 并输出: abcde
console.log( buf.toString(undefined,0,5)); // 使用默认的 'utf8' 编码, 并输出: abcde
```

执行以上代码，输出结果为：

```text
$ node main.js
abcdefghijklmnopqrstuvwxyz
abcde
abcde
abcde
```


## 将 Buffer 转换为 JSON 对象


### 语法

将 Node Buffer 转换为 JSON 对象的函数语法格式如下：

```text
buf.toJSON()
```

当字符串化一个 Buffer 实例时，JSON.stringify() 会隐式地调用该 toJSON()。


### 返回值

返回 JSON 对象。


### 实例

```html
const buf = Buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
const json = JSON.stringify(buf);

// 输出: {"type":"Buffer","data":[1,2,3,4,5]}
console.log(json);

const copy = JSON.parse(json, (key, value) => {
  return value && value.type === 'Buffer' ?
    Buffer.from(value.data) :
    value;
});

// 输出: <Buffer 01 02 03 04 05>
console.log(copy);
```

执行以上代码，输出结果为：

```html
{"type":"Buffer","data":[1,2,3,4,5]}
<Buffer 01 02 03 04 05>
```


## 缓冲区合并


### 语法

Node 缓冲区合并的语法如下所示：

```text
Buffer.concat(list[, totalLength])
```


### 参数

参数描述如下：

- list - 用于合并的 Buffer 对象数组列表。
- totalLength - 指定合并后Buffer对象的总长度。


### 返回值

返回一个多个成员合并的新 Buffer 对象。


### 实例

```javascript
var buffer1 = Buffer.from(('菜鸟教程'));
var buffer2 = Buffer.from(('www.runoob.com'));
var buffer3 = Buffer.concat([buffer1,buffer2]);
console.log("buffer3 内容: " + buffer3.toString());
```

执行以上代码，输出结果为：

```text
buffer3 内容: 菜鸟教程www.runoob.com
```


## 缓冲区比较


## 后续章节

- 语法
- 参数
- 返回值
- 实例
- 拷贝缓冲区
- 语法
- 参数
- 返回值
- 实例
- 缓冲区裁剪
- 参数
- 返回值
- 实例
- 缓冲区长度
- 语法
- 返回值

## 复习重点

- 能说明 `Node.js Buffer` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
