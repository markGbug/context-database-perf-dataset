# Playwright：Playwright CI/CD 集成

- 来源：[Playwright CI/CD 集成](https://www.runoob.com/playwright/playwright-ci-cd.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0541

## 本章内容

本章介绍如何将 Playwright 测试集成到 CI/CD 流水线中，包括 GitHub Actions 和其他常见 CI 平台。


## GitHub Actions 集成

当你在 npm init playwright@latest 时选择添加 GitHub Actions，Playwright 会自动生成工作流配置。


### 自动生成的工作流


## 实例


## 查看 CI 测试结果


### 查看测试日志

在 GitHub 仓库的 Actions 页面中，点击每次运行可以查看详细的测试日志。

每个 Worker 的输出都会独立显示，方便定位特定失败的测试。


### 查看 HTML 报告

如果配置了 reporter: 'html'，可以从 Artifacts 下载 playwright-report/ 来本地查看完整的 HTML 报告。


### 发布报告到 Web


## 实例


## 其他 CI 平台


### Jenkins

```text
pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        sh 'npm ci'
        sh 'npx playwright install --with-deps'
      }
    }
    stage('Test') {
      steps {
        sh 'npx playwright test'
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'playwright-report/**'
      junit 'test-results/junit.xml'
    }
  }
}
```


### GitLab CI


## 实例


## Docker 运行 Playwright

微软提供了预装所有系统依赖的官方 Docker 镜像，开箱即用。


### 使用官方镜像

```text
# 拉取镜像
docker pull mcr.microsoft.com/playwright:v1.52.0-jammy

# 在容器中运行测试
docker run --rm -v $(pwd):/work -w /work \
  mcr.microsoft.com/playwright:v1.52.0-jammy \
  npx playwright test
```


### Dockerfile 示例


## 实例


## CI 环境最佳实践


## 记忆卡片

- 一句话定义：`Playwright CI/CD 集成` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
