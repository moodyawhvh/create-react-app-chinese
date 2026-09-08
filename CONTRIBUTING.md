# Contributing to Create React App(参与贡献指南)

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

喜欢 Create React App 并想参与其中?谢谢!你可以通过很多方式提供帮助。

请花一点时间阅读本文档,让每个人的贡献流程都简单高效。

遵循这些准则,表示你尊重管理和开发这个开源项目的开发者的时间。相应地,他们在处理你的 issue、评审补丁和新功能时也会尊重你。

> 📝 **摘译说明**:本文超过 10000 字符,以下为全文核心章节的中文翻译;末尾「发布版本 / 发布文档」等维护者流程仅保留要点概述,细节请参阅英文原版。

## 核心理念(Core Ideas)

我们尽可能避免增加配置项和命令行标志。这个工具的目的是为 React 初学者提供最好的上手体验,这一点永远是第一优先级。这意味着有时我们会[主动舍弃一些额外功能](https://gettingreal.37signals.com/ch05_Half_Not_Half_Assed.php)(比如服务端渲染),因为很难在完全不引入配置的前提下把它做好。

我们更倾向于用**约定、启发式规则或交互**来代替配置。<br>
下面是几个实际例子。

### 约定(Convention)

<!--alex disable easy-->

我们不让用户指定入口文件名,而是始终假定它是 `src/index.js`;也不让用户指定输出的 bundle 名,而是自动生成,并确保其中包含内容哈希。只要可能,我们都希望借助约定替用户做出正确的选择,尤其是在容易配错的场景下。

### 启发式规则(Heuristics)

通常 `npm start` 运行在 `3000` 端口,这个端口不是显式可配置的。但某些环境(比如云端 IDE)希望程序跑在指定端口上以便输出结果。我们希望与各种环境良好配合,所以 Create React App 会读取 `PORT` 环境变量,并在它存在时优先使用。妙处在于:云端 IDE 会自动设置这个变量,用户什么都不用做。Create React App 依靠启发式规则根据环境自动做正确的事。

<!--alex disable just-->

另一个例子是 `npm test` 平时会启动监听模式,但如果设置了 `CI` 环境变量,就只跑一遍测试。主流 CI 环境都会设置这个变量,所以用户同样不需要做任何事,一切开箱即用。

### 交互(Interactivity)

我们更愿意给命令行界面增加交互,而不是加配置标志。例如 `npm start` 默认尝试使用 `3000` 端口,但端口可能被占用。很多工具在这种情况下直接失败,要求你换个端口重试;Create React App 则会弹出提示,询问你是否要在下一个可用端口上运行应用。

交互的另一个例子是 `npm test` 的监听界面。我们不让用户传命令行标志来切换测试模式或搜索模式,而是打印按键提示,你在测试过程中按下对应按键即可指挥监听器。Jest 同时支持标志和交互式 CLI,但 Create React App 更倾向于长时间运行的交互会话,让用户保持专注,而不是用各种标志跑短命会话。

### 打破规则(Breaking the Rules)

没有哪条规则是完美的。如果我们认为某个功能价值足够高、值得为此引入复杂度,也可能添加标志或配置。例如我们知道应用可能部署在根路径之外的子路径下,必须支持这种用例。但我们仍然尽量回退到启发式规则:这个例子里我们只要求你在 `package.json` 中指定 `homepage`,再据此推断正确的路径。构建结束后我们还会提示用户补填 `homepage`,让用户知道这个功能的存在。

## 提交 Pull Request(Submitting a Pull Request)

优秀的 PR——补丁、改进、新功能——是巨大的帮助。它们应当聚焦在单一范围内,避免混入无关的提交。

请**先询问**:是否已经有人在处理同样的事,以及核心开发者是否认为你的功能在 Create React App 的范围之内。一般来说,你要包含的内容都应该有一个相关的 issue 及其讨论。

同时请提供**测试计划(test plan)**,即说明你如何验证你的改动确实有效。

## Create React App 的目录结构(Folder Structure)

`create-react-app` 是一个 monorepo,也就是被拆分成多个独立的子包。<br>
这些包位于 [`packages/`](https://github.com/facebook/create-react-app/tree/main/packages) 目录。

### 目录结构总览

```
packages/
  babel-plugin-named-asset-import/
  babel-preset-react-app/
  confusing-browser-globals/
  cra-template/
  cra-template-typescript/
  create-react-app/
  eslint-config-react-app/
  react-app-polyfill/
  react-dev-utils/
  react-error-overlay/
  react-scripts/
```

### 各包说明(Package Descriptions)

#### [babel-preset-react-app](https://github.com/facebook/create-react-app/tree/main/packages/babel-preset-react-app)

配合 `react-scripts` 使用的 babel preset。<br>
面向 React 官方支持的平台(IE 11+),并启用 Facebook 内部大量使用的实验性特性。<br>
所有 `create-react-app` 脚手架生成的应用默认启用此包。

#### [create-react-app](https://github.com/facebook/create-react-app/tree/main/packages/create-react-app)

全局 CLI 命令的代码在这个目录里,一般不需要改动。它需要兼容 Node 0.10+。

#### [eslint-config-react-app](https://github.com/facebook/create-react-app/tree/main/packages/eslint-config-react-app)

一套保守的 ESLint 规则,聚焦于让错误显形,不强制代码风格。<br>
所有 `create-react-app` 脚手架生成的应用默认启用此包。

#### [react-dev-utils](https://github.com/facebook/create-react-app/tree/main/packages/react-dev-utils)

`react-scripts` 及兄弟包使用的工具集。<br>
主要目的是把用户不必关心的代码隐藏起来,直到用户选择 eject。

#### [react-scripts](https://github.com/facebook/create-react-app/tree/main/packages/react-scripts)

整个项目的心脏,包含启动开发服务器、构建生产版本、配置所用各种工具的脚本。<br>
用户选择 eject 时,必须保留全部功能(并把配置交还给用户)。

## 搭建本地副本(Setting Up a Local Copy)

你需要 `npm@7` 和 `yarn@1` 来初始化并测试本仓库的本地副本。

1. `git clone https://github.com/facebook/create-react-app` 克隆仓库

2. 在根目录 `create-react-app` 下运行 `npm install`。

完成后,你可以修改任意文件,然后像在生成的项目里一样运行 `npm start`、`npm test` 或 `npm run build`。它会以 `packages/cra-template/template` 中的文件来运行应用。

如果你想通过全局 CLI 体验完整的端到端流程,也可以:

```sh
npx create-react-app my-app
cd my-app
```

然后运行 `npm start` 或 `npm run build`。

## 参与 E2E(端到端)测试

**TL;DR**:使用命令 `npm run e2e:docker` 运行单元测试和 e2e 测试。

更多细节见专门的 [README](/test/README.md)。

### 使用私有包进行 CI 测试

**create-react-app** 默认从主 registry 拉取全部依赖;但如果你需要在 E2E 测试运行期间拉取自定义的私有包,可能需要一套不同的配置。

#### 自定义 E2E registry 配置

我们用 [verdaccio](https://github.com/verdaccio/verdaccio) 以默认配置模拟包发布到 registry。你可以通过编辑 `task/verdaccio.yaml` 来修改这一行为。

配置详情请查阅 [Verdaccio 文档](https://verdaccio.org/docs/en/configuration)。

## Windows 贡献者提示

tasks 目录下的脚本以及 `package.json` 里的其他脚本在 Windows 上默认无法直接运行。不过,使用 [Windows 上的 Bash](https://msdn.microsoft.com/en-us/commandline/wsl/about) 可以让你无需任何变通方法就能使用这些脚本。步骤如下:

### 在 Windows 上安装 Ubuntu Bash

不错的分步教程见[这里](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)

### 安装 Node.js 和 yarn

即使你在 Windows 上已经装了 node 和 yarn,Bash shell 里也访问不到它们,需要重新安装一遍。推荐通过 [`nvm`](https://github.com/creationix/nvm#install-script) 安装。

### 行尾符(Line endings)

git 默认使用 `CRLF` 行尾符,这会导致脚本失败。你可以只为本仓库设置 `autocrlf` 为 false:运行 `git config core.autocrlf false`。也可以加上 `--global` 标志对你所有的仓库生效。

## 发布版本(Cutting a Release)——要点概述

1. 用相应的 milestone 标记所有进入本次发布的已合并 PR,并打上 `tag: ...` 标签;**破坏性变更必须打上 `tag: breaking change`。**
2. 关闭当前 milestone,为下一个版本创建新的 milestone。
3. 大多数版本只需发布 `react-scripts`;`packages/create-react-app` 无改动时不必升版发布。
4. `packages/create-react-app` 的文件修改须极其谨慎:作为全局 CLI,任何旧版本都必须兼容最新的 `react-scripts`。
5. 拉取最新代码,运行 `npm ci`。
6. 用 `npm run changelog` 生成变更日志条目(需先 `export GITHUB_AUTH="..."` 提供 GitHub API token),手工润色后粘贴到 `CHANGELOG.md`;每个重要条目补充四空格缩进的说明段,破坏性变更还要写明影响对象和迁移步骤。
7. 为上一个版本附上「Migrating from ...」迁移说明,通常可直接复制。
8. 运行 `npm run publish`(必须是这个命令,不是 `npm publish` 或 `yarn publish`)。
9. 耐心等待,发布脚本最后会在发布前提示确认各包版本。
10. 发布后,用与 changelog 相同的文本创建 GitHub Release。

务必测试发布后的版本!想更稳妥的话,可用 `npm run publish -- --canary --exact --preid next --dist-tag=next --force-publish=* minor` 先发预发布版本。

## 发布文档(Releasing the Docs)——要点概述

1. 进入 `docusaurus/website` 目录
2. 运行 `npm ci`
3. 运行 `npm run build`
4. 需要 [GitHub API 的 access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/),保存到环境变量:`export GITHUB_AUTH="..."`
5. 运行 `GIT_USER=<GITHUB_USERNAME> CURRENT_BRANCH=main USE_SSH=true npm run deploy`

---

_许多灵感来自 [h5bp](https://github.com/h5bp/html5-boilerplate/blob/master/.github/CONTRIBUTING.md) 的贡献指南,特此感谢_
