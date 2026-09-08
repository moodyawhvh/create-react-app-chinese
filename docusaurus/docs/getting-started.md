---
id: getting-started
title: 快速上手
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

Create React App 是官方支持的创建 React 单页应用的方式。它提供开箱即用的现代构建配置,无需任何配置。

## 快速开始

```sh
npx create-react-app my-app
cd my-app
npm start
```

> 如果你之前通过 `npm install -g create-react-app` 全局安装过 `create-react-app`,建议先用 `npm uninstall -g create-react-app` 或 `yarn global remove create-react-app` 卸载它,以确保 `npx` 始终使用最新版本。

_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) 自 npm 5.2+ 起内置,旧版 npm 的[安装说明见此](https://gist.github.com/gaearon/4064d3c23a77c74a3614c498a8bb1c5f))_

然后打开 [http://localhost:3000/](http://localhost:3000/) 查看你的应用。

当你准备好部署到生产环境时,用 `npm run build` 生成压缩后的构建产物。

<p align='center'>
<img src='https://cdn.jsdelivr.net/gh/facebook/create-react-app@27b42ac7efa018f2541153ab30d63180f5fa39e0/screencast.svg' width='600' alt='npm start' />
</p>

### 立即开始

你**不需要**安装或配置 webpack、Babel 之类的工具。它们已经预先配置好并对用户隐藏,让你可以专注于代码本身。

创建一个项目,就可以直接开写。

## 创建应用

**你的本地开发机需要 Node >= 14**(服务器上不作要求)。你可以用 [nvm](https://github.com/creationix/nvm#installation)(macOS/Linux)或 [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) 在不同项目间切换 Node 版本。

创建新应用,可以选择以下任意一种方式:

### npx

```sh
npx create-react-app@latest my-app
```

_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) 自 npm 5.2+ 起内置,旧版 npm 的[安装说明见此](https://gist.github.com/gaearon/4064d3c23a77c74a3614c498a8bb1c5f))_

### npm

```sh
npm init react-app my-app
```

_`npm init <initializer>` 在 npm 6+ 可用_

### Yarn

```sh
yarn create react-app my-app
```

_`yarn create` 在 Yarn 0.25+ 可用_

### 选择模板

现在你可以在创建命令后追加 `--template [template-name]`,选择从一个模板启动新应用。

如果不选模板,我们会用基础模板创建你的项目。

模板的包名始终是 `cra-template-[template-name]` 格式,但创建命令中只需要提供 `[template-name]` 部分。

```sh
npx create-react-app my-app --template [template-name]
```

> 在 npm 上搜索 ["cra-template-\*"](https://www.npmjs.com/search?q=cra-template-*) 可以找到可用模板列表。

我们的[自定义模板](custom-templates.md)文档介绍了如何构建你自己的模板。

#### 创建 TypeScript 应用

你可以通过模板创建新的 TypeScript 应用。要使用官方 TypeScript 模板,在创建命令后追加 `--template typescript`。

```sh
npx create-react-app my-app --template typescript
```

如果你已有项目并想添加 TypeScript,请参阅[添加 TypeScript](adding-typescript.md)文档。

### 选择包管理器

创建新应用时,CLI 会根据你运行 `create-react-app` 所用的工具,使用 [npm](https://docs.npmjs.com) 或 [Yarn](https://yarnpkg.com/) 安装依赖。例如:

```sh
# 运行这条命令使用 npm
npx create-react-app my-app
# 或者运行这条命令使用 yarn
yarn create react-app my-app
```

## 输出结果

运行上述任意命令,都会在当前目录下创建一个名为 `my-app` 的目录。该目录内会生成初始项目结构,并安装传递依赖:

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

没有配置,没有复杂的目录结构,只有构建应用所需的文件。安装完成后,进入项目目录:

```sh
cd my-app
```

## 脚本命令

在新创建的项目里,你可以运行这些内置命令:

### `npm start` 或 `yarn start`

以开发模式运行应用。打开 [http://localhost:3000](http://localhost:3000) 在浏览器中查看。

修改代码后页面会自动刷新。你会在控制台看到构建错误和 lint 警告。

<p align='center'>
<img src='https://cdn.jsdelivr.net/gh/marionebl/create-react-app@9f6282671c54f0874afd37a72f6689727b562498/screencast-error.svg' width='600' alt='Build errors' />
</p>

### `npm test` 或 `yarn test`

以交互模式运行测试监听器。默认只运行与自上次提交以来改动过的文件相关的测试。

[了解更多关于测试的内容](running-tests.md)。

### `npm run build` 或 `yarn build`

为生产环境构建应用到 `build` 文件夹。它会以生产模式正确打包 React,并为最佳性能优化构建。

构建产物经过压缩,文件名包含内容哈希。

你的应用已准备好部署。
