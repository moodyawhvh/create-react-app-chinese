<div align="center">

# create-react-app 中文翻译版

**[中文版] create-react-app — 一条命令即可搭建现代 React Web 应用**

[![原项目](https://img.shields.io/badge/原项目-react--create-react-app-blue?style=flat-square&logo=github)](https://github.com/react/create-react-app)
[![中文文档](https://img.shields.io/badge/中文文档-README.zh--CN.md-orange?style=flat-square)](README.zh-CN.md)
[![GitHub Stars](https://img.shields.io/github/stars/react/create-react-app?style=flat-square&label=原项目Stars)](https://github.com/react/create-react-app/stargazers)
[![微信联系](https://img.shields.io/badge/微信-uaycar-brightgreen?style=flat-square&logo=wechat)](#)

</div>

---

> 这是 [react/create-react-app](https://github.com/react/create-react-app) 的中文翻译版本。
> 完整源代码请访问原项目:https://github.com/react/create-react-app

**代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**

---

## 📖 项目简介

Create React App(即 `create-react-app`)是 React 官方生态中最经典的脚手架工具:无需手动配置 webpack、Babel 等构建工具,只需运行一条命令,就能在本地生成一个开箱即用的现代 React 单页应用开发环境。它曾是 2017-2021 年间启动 React 项目的首选方案。目前该项目已进入长期维护停滞状态,官方建议新项目迁移到 react.dev 推荐的各类 React 框架,但文档中的实践思路对学习 React 仍有很高参考价值。

## ✨ 主要特性

- **零构建配置**:一条命令创建 React 应用,webpack / Babel 等已预配置并隐藏,专注写代码即可。
- **单一依赖**:只有一个构建依赖,内部整合 webpack、Babel、ESLint 等优秀项目,提供统一顺滑的体验。
- **随时 eject 不锁定**:运行单条命令即可把全部配置和构建依赖"弹出"到项目里,自由定制。
- **开箱即用的技术栈**:支持 React、JSX、ES6、TypeScript 与 Flow 语法,以及对象展开运算符等 ES6+ 特性。
- **CSS 自动前缀**:Autoprefixer 自动处理 `-webkit-` 等浏览器前缀。
- **快速交互式测试**:内置单元测试运行器,支持覆盖率报告。
- **实时开发服务器**:修改代码自动刷新,常见错误即时警告,构建错误与 lint 提醒直接显示在控制台。
- **生产级构建脚本**:一键打包 JS、CSS 与图片,输出带哈希文件名与 sourcemap 的优化产物。
- **PWA 支持**:离线优先的 Service Worker 与 Web App Manifest,满足渐进式 Web 应用标准(自 `react-scripts@2.0.0` 起为可选开启)。

## 📁 文件说明

| 文件 | 说明 |
|:-----|:-----|
| README.md | 本文件(中文简介) |
| README.zh-CN.md | 详细中文文档(完整汉化) |

## 🚀 快速开始

**环境要求**:本地开发机需安装 Node 14.0.0 或更高版本(服务器端不要求),建议使用最新 LTS 版本。可用 [nvm](https://github.com/nvm-sh/nvm#installation)(macOS/Linux)或 [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) 在不同项目间切换 Node 版本。

1. 创建新应用(三选一):

```sh
npx create-react-app my-app
```

```sh
npm init react-app my-app
```

```sh
yarn create react-app my-app
```

2. 进入项目目录:

```sh
cd my-app
```

3. 启动开发服务器:

```sh
npm start
```

打开 [http://localhost:3000](http://localhost:3000) 即可在浏览器中查看应用,修改代码后页面自动刷新。

4. 构建生产版本:

```sh
npm run build
```

构建产物输出到 `build` 文件夹,已压缩优化,可直接部署。

> 提示:如果之前通过 `npm install -g create-react-app` 全局安装过旧版本,建议先 `npm uninstall -g create-react-app` 卸载,确保 npx 始终使用最新版本。

完整源代码与最新版本请访问原项目:https://github.com/react/create-react-app

## 📞 联系方式

**代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**

---

本项目为 [react/create-react-app](https://github.com/react/create-react-app) 的中文翻译版本,所有代码版权归原项目作者所有,遵循其原始许可证(MIT)。

**如果觉得有用,请给原项目点个 Star!** ⭐
