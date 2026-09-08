---
id: available-scripts
title: 可用脚本
sidebar_label: 可用脚本
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

在项目目录下,你可以运行:

## `npm start`

以开发模式运行应用。打开 [http://localhost:3000](http://localhost:3000) 在浏览器中查看。

编辑代码后页面会自动刷新,控制台中还会显示 lint 错误。

## `npm test`

以交互式监听模式启动测试运行器。更多信息参见[运行测试](running-tests.md)一节。

## `npm run build`

为生产环境构建应用到 `build` 文件夹。它会以生产模式正确打包 React,并为最佳性能优化构建。

构建产物经过压缩,文件名包含内容哈希。如有需要,可以启用类名和函数名用于性能分析。更多信息参见[生产构建](production-build.md)一节。

你的应用已准备好部署!关于如何把应用部署到主流托管服务商,参见[部署](deployment.md)一节。

## `npm run eject`

**注意:这是单向操作。一旦 `eject`,无法回头!**

如果你对构建工具和配置选项不满意,可以随时 `eject`。该命令会从项目中移除这个单一的构建依赖。

取而代之,它会把所有配置文件和传递依赖(webpack、Babel、ESLint 等)直接复制到你的项目中,作为 `package.json` 里的依赖。从技术上讲,对于产出静态 bundle 的前端应用来说,dependencies 和 devDependencies 的区分相当随意。

此外,这曾经在某些不安装开发依赖的托管平台上引发问题(导致无法在服务器上构建项目或在部署前进行测试)。你可以随意按自己的需要重新整理 `package.json` 中的依赖。

除 `eject` 之外的所有命令仍然可用,只是它们会指向复制出来的脚本,方便你自行调整。从这一刻起,一切靠自己。

你完全不必使用 `eject`。这套精选的功能集适合中小型部署,不要觉得有义务使用这个功能。不过我们也明白:如果你准备好的时候无法自定义,这个工具就没有意义了。
