---
id: updating-to-new-releases
title: 升级到新版本
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

Create React App 分为两个包:

- `create-react-app` 是全局命令行工具,用来创建新项目。
- `react-scripts` 是生成项目(包括本项目)中的开发依赖。

当你运行 `npx create-react-app my-app` 时,它会自动安装最新版本的 Create React App。

> 如果你之前通过 `npm install -g create-react-app` 全局安装过 `create-react-app`,请访问[快速上手](getting-started.md)了解当前的安装步骤。

Create React App 会用最新版的 `react-scripts` 创建项目,因此新建的应用会自动获得所有新特性和改进。

要把已有项目升级到新版 `react-scripts`,请[打开变更日志](https://github.com/facebook/create-react-app/blob/main/CHANGELOG.md),找到你当前使用的版本(不确定就查看本目录下的 `package.json`),然后按新版本的迁移说明操作。

大多数情况下,只需在 `package.json` 中提升 `react-scripts` 的版本号,然后在本目录运行 `npm install`(或 `yarn install`)即可,但最好还是查阅[变更日志](https://github.com/facebook/create-react-app/blob/main/CHANGELOG.md)确认是否存在破坏性变更。

我们承诺把破坏性变更降到最少,让你可以无痛升级 `react-scripts`。
