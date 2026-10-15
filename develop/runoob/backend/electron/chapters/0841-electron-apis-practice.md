# Electron：Electron API 速查与配置模板

- 来源：[Electron API 速查与配置模板](https://www.runoob.com/electron/electron-apis.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0841

## 本章内容

## 主进程 API 速查表


## 渲染进程 API 速查表


## 常用辅助模块速查表


## 配置文件模板与说明


### package.json 模板与说明

```text
{
  "name": "my-electron-app",
  "version": "1.0.0",
  "description": "示例 Electron 应用",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "pack": "electron-builder --dir",
    "dist": "electron-builder"
  },
  "devDependencies": {
    "electron": "^33.0.0",
    "electron-builder": "^24.6.0"
  },
  "build": {
    "appId": "com.example.myelectronapp",
    "productName": "MyElectronApp",
    "directories": {
      "output": "dist"
    },
    "files": [
      "main.js",
      "preload.js",
      "renderer/**/*"
    ],
    "win": {
      "target": "nsis",
      "icon": "assets/icon.ico"
    },
    "mac": {
      "category": "public.app-category.productivity",
      "icon": "assets/icon.icns"
    },
    "linux": {
      "target": "AppImage",
      "icon": "assets/"
    }
  }
}
```

说明：


### electron-builder.yml 模板与说明

```text
appId: com.example.myelectronapp
productName: MyElectronApp
directories:
  output: dist
files:
  - "main.js"
  - "preload.js"
  - "renderer/**/*"
win:
  target: nsis
  icon: assets/icon.ico
mac:
  target: dmg
  icon: assets/icon.icns
linux:
  target: AppImage
  icon: assets/
publish:
  provider: github
  repo: my-electron-app
  owner: username
```

说明：


### TypeScript tsconfig.json 模板与说明

```text
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "esModuleInterop": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "skipLibCheck": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

说明：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron API 速查与配置模板` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
