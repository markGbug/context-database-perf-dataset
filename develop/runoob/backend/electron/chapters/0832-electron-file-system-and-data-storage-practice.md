# Electron：Electron 文件系统与数据存储

- 来源：[Electron 文件系统与数据存储](https://www.runoob.com/electron/electron-file-system-and-data-storage.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0832

## 本章内容

在 Electron 中，由于它基于 Node.js，你可以直接访问文件系统、数据库以及本地存储。

这让桌面应用能够像传统软件一样读写文件、保存配置，甚至实现复杂的数据管理。


## 文件系统操作

Electron 允许你在渲染进程或主进程中使用 Node.js 的内置 fs 模块进行文件操作。


### Node.js fs 模块的使用

fs 模块提供了多种文件系统操作，如读取、写入、重命名、删除等。


## 实例

参数说明：

- fs.readFile(path, encoding, callback)：异步读取文件内容。
- fs.writeFile(path, data, callback)：写入文件（若不存在则自动创建）。
- path.join()：组合路径，跨平台兼容。


### 文件监听

可以使用 fs.watch 实时监听文件变化，例如用于检测配置文件或数据文件更新：

```javascript
fs.watch(filePath, (eventType, filename) => {
  console.log(`文件变化类型: ${eventType}`);
  console.log(`变化的文件: ${filename}`);
});
```


### 应用目录路径

Electron 提供 app.getPath(name) 方法来获取常用系统路径：

```javascript
const { app } = require('electron');

console.log(app.getPath('home'));       // 用户主目录
console.log(app.getPath('desktop'));    // 桌面路径
console.log(app.getPath('userData'));   // 应用数据目录
```

这些路径可以用来存放日志、缓存或用户配置文件。


## 本地数据存储

Electron 应用通常需要保存用户配置、缓存或状态信息。常见的存储方式包括：


### localStorage 与 sessionStorage

适用于简单的键值对数据，例如主题设置、窗口状态等：

```javascript
localStorage.setItem('theme', 'dark');
const theme = localStorage.getItem('theme');
console.log(theme);
```

区别：

- localStorage：永久存储，关闭应用后仍保留。
- sessionStorage：会话级存储，关闭窗口即清除。


### IndexedDB 数据库

适合存储结构化数据，适用于离线应用：


## 实例


### electron-store 使用

electron-store 是最方便的配置存储库，基于 JSON 自动持久化。

安装：

```text
npm install electron-store
```

使用示例：


## 实例

优点：

- 自动保存到用户数据目录；
- JSON 格式，直观易编辑；
- 适用于小型持久化存储（设置、缓存等）。


### 数据持久化方案建议


## 数据库集成

当应用需要存储大量或关系型数据时，可以集成数据库。


### SQLite 集成

SQLite 是 Electron 应用最常用的嵌入式数据库。 安装依赖：

```text
 npm install sqlite3
```

示例代码：


## 实例


### LevelDB 使用

LevelDB 是键值型数据库，适合缓存与高性能读写。

安装：

```text
npm install level
```

使用示例：


## 实例


### 其他数据库选择


## 综合小结

在 Electron 中，数据存储方案灵活多样：

- 小数据 → electron-store；
- 大数据 → SQLite；
- 结构化 → IndexedDB；
- 高速键值 → LevelDB；
- 文件型 → fs + JSON。

这使 Electron 应用既能轻量运行，也能承载复杂的业务逻辑与数据存储任务。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 文件系统与数据存储` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
