<div align="center">

# create-react-app 中文文档

[![原项目](https://img.shields.io/badge/原项目-facebook--create--react--app-blue?style=flat-square&logo=github)](https://github.com/react/create-react-app)
[![微信联系](https://img.shields.io/badge/微信-uaycar-brightgreen?style=flat-square&logo=wechat)](#)

</div>

> 本文档是 [react/create-react-app](https://github.com/react/create-react-app) 官方 README 的中文翻译版本,版权归原作者所有。

> [!WARNING]
> ## ⚠️ 已弃用(Deprecated)
>
> Create React App 是 2017-2021 年间启动 React 项目的核心工具,目前处于长期停滞状态。官方建议迁移到 [Start a New React Project](https://react.dev/learn/start-a-new-react-project) 中推荐的 React 框架。如果你在跟着教程学习 React,继续完成教程仍有价值,但不建议基于它启动生产应用。

Create React 应用,无需任何构建配置。

- [创建应用](#创建应用) — 如何创建一个新应用。
- [用户指南](https://facebook.github.io/create-react-app/) — 如何开发由 Create React App 引导的应用。

Create React App 支持 macOS、Windows 和 Linux。遇到问题请[提交 issue](https://github.com/facebook/create-react-app/issues/new),有疑问可在 [GitHub Discussions](https://github.com/facebook/create-react-app/discussions) 提问。

## 快速概览

```sh
npx create-react-app my-app
cd my-app
npm start
```

如果你之前通过 `npm install -g create-react-app` 全局安装过,建议用 `npm uninstall -g create-react-app` 或 `yarn global remove create-react-app` 卸载,确保 npx 始终使用最新版本。_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) 随 npm 5.2+ 提供)_

然后打开 [http://localhost:3000/](http://localhost:3000/) 查看你的应用。准备部署到生产环境时,使用 `npm run build` 生成压缩后的构建产物。

### 立即上手

你**不需要**安装或配置 webpack、Babel 等工具,它们已预配置并隐藏,让你专注于代码本身。创建项目,直接开干。

## 创建应用

**本地开发机需要 Node 14.0.0 或更高版本**(服务器端不要求),建议使用最新 LTS 版本,可用 [nvm](https://github.com/creationix/nvm#installation)(macOS/Linux)或 [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) 切换版本。

创建新应用可任选以下方式之一:

### npx

```sh
npx create-react-app my-app
```

### npm

```sh
npm init react-app my-app
```

_`npm init <initializer>` 需要 npm 6+_

### Yarn

```sh
yarn create react-app my-app
```

_`yarn create <starter-kit-package>` 需要 Yarn 0.25+_

它会在当前目录下创建名为 `my-app` 的目录,并生成初始项目结构、安装传递依赖:

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public        # favicon.ico / index.html / manifest.json
└── src           # App.js、index.js、logo.svg、测试与样式文件等
```

没有复杂配置和目录结构,只有构建应用所需的文件。安装完成后,进入项目文件夹:

```sh
cd my-app
```

在新创建的项目中,可以运行以下内置命令:

### `npm start` 或 `yarn start`

以开发模式运行应用。<br>
打开 [http://localhost:3000](http://localhost:3000) 在浏览器中查看。

修改代码后页面会自动刷新。<br>
构建错误和 lint 警告会直接显示在控制台中。

### `npm test` 或 `yarn test`

以交互模式运行测试监视器。<br>
默认只运行与上次提交以来修改过的文件相关的测试。

[了解更多测试相关内容。](https://facebook.github.io/create-react-app/docs/running-tests)

### `npm run build` 或 `yarn build`

为生产环境构建应用到 `build` 文件夹,以生产模式打包 React 并针对最佳性能优化。产物经过压缩,文件名包含哈希值,可直接部署上线。

## 用户指南

关于 Create React App 的详细使用说明和技巧,请参阅[官方文档](https://facebook.github.io/create-react-app/)。

## 如何更新到新版本?

请参阅[用户指南](https://facebook.github.io/create-react-app/docs/updating-to-new-releases)获取相关信息。

## 设计哲学

- **单一依赖:** 只有一个构建依赖。它内部使用 webpack、Babel、ESLint 等优秀项目,但在其之上提供了统一、精心打磨的体验。

- **零配置:** 无需配置任何东西。开发与生产构建的合理默认配置已替你完成,你可以专注写代码。

- **不被锁定:** 任何时候都可以"eject"到自定义配置。运行单条命令,所有配置和构建依赖会直接移入你的项目,从当前进度无缝接管。

## 包含了什么?

你的环境将拥有构建现代 React 单页应用所需的一切:

- 支持 React、JSX、ES6、TypeScript 和 Flow 语法。
- 支持 ES6 之外的语言扩展,如对象展开运算符。
- CSS 自动前缀,无需手写 `-webkit-` 等前缀。
- 快速的交互式单元测试运行器,内置覆盖率报告支持。
- 实时开发服务器,对常见错误发出警告。
- 生产构建脚本,打包 JS、CSS 和图片,带哈希文件名和 sourcemap。
- 离线优先的 [Service Worker](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers) 和 [Web App Manifest](https://developers.google.com/web/fundamentals/engage-and-retain/web-app-manifest/),满足全部[渐进式 Web 应用](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)标准。(_注意:自 `react-scripts@2.0.0` 起,Service Worker 为可选启用_)
- 上述工具可通过单一依赖轻松更新。

想知道这些工具如何协同工作,可查看[这份指南](https://github.com/nitishdayal/cra_closer_look)。

代价是**这些工具被预配置为特定的工作方式**。如果你的项目需要更多定制,可以 ["eject"](https://facebook.github.io/create-react-app/docs/available-scripts#npm-run-eject) 后自行修改,但之后需要自己维护这些配置。

## 适用场景与替代方案

Create React App 非常适合:

- 在舒适且功能齐全的开发环境中**学习 React**。
- **启动新的单页 React 应用。**
- 为你的库和组件**创建 React 示例**。

以下常见情况建议尝试其他方案:

- 想**体验 React** 但不想引入上百个构建依赖?考虑[用单个 HTML 文件或在线沙盒](https://reactjs.org/docs/getting-started.html#try-react)。
- 需要**集成服务端模板框架**(Rails/Django/Symfony)或**不做单页应用**?考虑更灵活的 [nwb](https://github.com/insin/nwb) 或 [Neutrino](https://neutrino.js.org/);Rails 也可用 [Rails Webpacker](https://github.com/rails/webpacker)。
- 需要**发布 React 组件库**?[nwb](https://github.com/insin/nwb) 和 [Neutrino 的 react-components 预设](https://neutrino.js.org/packages/react-components/)都可以做到。
- 想做**服务端渲染**?看看 [Next.js](https://nextjs.org/) 或 [Razzle](https://github.com/jaredpalmer/razzle)。Create React App 与后端无关,只产出静态 HTML/JS/CSS。
- 网站**以静态内容为主**(作品集、博客)?考虑 [Gatsby](https://www.gatsbyjs.org/) 或 [Next.js](https://nextjs.org/),它们支持构建时预渲染。

以上工具几乎都无需配置即可使用。如果你更愿意自己配置构建,请[参考这份指南](https://reactjs.org/docs/add-react-to-a-website.html)。

## React Native

想找类似的 React Native 工具?<br>
看看 [Expo CLI](https://github.com/expo/expo-cli)。

## 参与贡献

欢迎为 `create-react-app` 出一份力!详见 [CONTRIBUTING.md](https://github.com/facebook/create-react-app/blob/main/CONTRIBUTING.md)。

## 支持 Create React App

Create React App 是社区维护的项目,贡献者均为志愿者。想支持它可以考虑通过 [Open Collective](https://opencollective.com/create-react-app) 捐赠。

## 致谢

本项目的发展离不开所有[贡献者](https://github.com/facebook/create-react-app/graphs/contributors),同时感谢 [Netlify](https://www.netlify.com/) 为文档提供托管,以及相关项目作者 [@eanplatter](https://github.com/eanplatter)、[@insin](https://github.com/insin)、[@mxstbr](https://github.com/mxstbr) 的思路与协作。

## 许可证

Create React App 是基于 [MIT 许可证](https://github.com/facebook/create-react-app/blob/main/LICENSE)的开源软件。Create React App 的 Logo 采用 [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) 许可。

---

> **版权声明**:本文档为 [react/create-react-app](https://github.com/react/create-react-app) 官方 README 的中文翻译,所有代码与原文版权归原项目作者所有,遵循其原始 MIT 许可证。
>
> **代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**
>
> **如果觉得有用,请给原项目点个 Star!** ⭐
