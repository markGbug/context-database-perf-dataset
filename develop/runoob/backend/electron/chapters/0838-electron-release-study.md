# Electron：Electron 发布与部署

- 来源：[Electron 发布与部署](https://www.runoob.com/electron/electron-release.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：学习笔记
- 章节序号：0838

## 本章内容

Electron 应用开发完成并打包后，需要将应用发布到用户端。发布方式主要分为 应用商店 和 独立分发，同时需要考虑更新服务和版本管理策略。


## 应用商店发布


### Microsoft Store 发布

- 打包要求：使用 electron-windows-store 工具将 .exe 或 .msix 转换为 Store 包
- 签名：需要 Microsoft Developer 账号并申请代码签名证书

流程：

- 生成 MSIX 包
- 在 Store Partner Center 上传
- 填写应用信息、截图和分类
- 提交审核


### Mac App Store 发布

- 打包要求：必须使用 .pkg 或 .app，且启用 Apple 公证（Notarization）
- 签名：Apple Developer 账号申请开发者证书

流程：

- 打包并签名应用
- 使用 Xcode 或 Transporter 上传
- 提交应用信息和截图
- 审核通过后上架


### Snap Store 发布（Linux）

打包要求：使用 Snapcraft 打包应用为 .snap 格式。

流程：

- 编写 snapcraft.yaml 配置
- 打包生成 .snap
- 在 Snapcraft Store 上传
- 审核通过后发布


### 审核准备

- 应用图标和截图符合商店要求
- 提交应用说明、分类、隐私政策
- 通过自动化或手动测试确保稳定性
- 避免应用使用不允许的 API 或权限


## 独立分发


### 官网下载

- 将打包好的 .exe、.dmg、.AppImage 放在官网提供下载
- 可结合 CDN 提供稳定下载速度
- 可提供 SHA256 或 MD5 校验，确保文件完整性


### GitHub Releases

- 使用 GitHub Releases 上传各平台安装包
- 可以结合 electron-updater 实现自动更新
- 优点：免费、易于管理版本


### CDN 分发

- 对大流量应用推荐使用 CDN
- 可提供跨区域快速下载
- 与自动更新服务器结合，实现差分更新


## 更新服务搭建


### 使用第三方服务

- 服务提供自动更新托管，例如： GitHub Releases + electron-updater AWS S3 + CloudFront Netlify / Vercel 静态托管


### 自建更新服务器

- 部署简单的 HTTP 或 HTTPS 服务
- 提供 JSON 更新描述文件（包含版本号、下载地址、更新日志）
- 支持差分更新，减少用户下载流量

示例 latest.yml 文件：

```text
version: 1.0.2
files:
  - url: MyElectronApp-1.0.2.exe
    sha512: "文件哈希值"
releaseDate: "2025-10-15T00:00:00Z"
```


### 版本管理策略

- 语义化版本（SemVer）：主版本.次版本.修订号
- 发布策略： 小版本：修复 bug 大版本：增加新功能或 UI 改动
- 自动更新策略： 启动检查更新 定期轮询更新 用户手动触发


## 小结

Electron 发布与部署核心流程：

- 应用商店：严格审核、签名、平台打包要求
- 独立分发：官网、GitHub Releases、CDN 提供下载
- 更新服务：自动更新、差分更新、版本管理策略

通过合理的发布和更新策略，可以确保用户获取最新、稳定、安全的应用版本，同时提升用户体验和应用维护效率。


## 复习重点

- 能说明 `Electron 发布与部署` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
