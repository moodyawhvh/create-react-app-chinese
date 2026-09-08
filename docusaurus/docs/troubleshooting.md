---
id: troubleshooting
title: 故障排查
sidebar_label: 故障排查
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

## `npm start` 检测不到改动

`npm start` 运行期间保存文件时,浏览器应当用更新后的代码自动刷新。

如果没有发生,请尝试以下变通方法:

- 检查你的文件是否被入口文件引入。TypeScript 会在任何源文件上显示错误,但 webpack 只有在文件被入口直接或间接引入时才会重新加载它。
- 如果你的项目放在 Dropbox 文件夹里,试着把它移出去。
- 如果监听器没有看到名为 `index.js` 的文件而你又是通过文件夹名引用它的,由于 webpack 的一个 bug,你[需要重启监听器](https://github.com/facebook/create-react-app/issues/1164)。
- 一些编辑器(如 Vim 和 IntelliJ)有「安全写入(safe write)」功能,目前会破坏监听器,你需要禁用它。操作方法见 [「调整你的文本编辑器」](https://webpack.js.org/guides/development/#adjusting-your-text-editor)。
- 如果你的项目路径包含括号,试着把项目移到不含括号的路径下。这是由 [webpack 监听器 bug](https://github.com/webpack/watchpack/issues/42) 引起的。
- 在 Linux 和 macOS 上,你可能需要[调整系统设置](https://github.com/webpack/docs/wiki/troubleshooting#not-enough-watchers)以允许更多监听器。
- 如果项目运行在虚拟机中(比如 Vagrant 配置的 VirtualBox),请在项目目录下创建一个 `.env` 文件(如果不存在),并加入 `CHOKIDAR_USEPOLLING=true`。这样下次运行 `npm start` 时,监听器会使用轮询模式,这是虚拟机内所必需的。

如果这些办法都无效,请[在这个帖子](https://github.com/facebook/create-react-app/issues/659)里留言。

## `npm start` 因监听错误而失败

如果你使用 Linux 操作系统,看到类似 `ENOSPC: System limit for number of file watchers reached` 的错误,可以通过提高操作系统的 `fs.inotify.max_user_watches` 设置来解决。

如果你使用 Debian、RedHat 或其他类似的 Linux 发行版,在终端运行:

```sh
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```

如果你使用 ArchLinux,改为运行以下命令:

```sh
echo fs.inotify.max_user_watches=524288 | sudo tee /etc/sysctl.d/40-max-user-watches.conf && sudo sysctl --system
```

把它粘贴到终端并回车执行。更多信息见[这里](https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers#the-technical-details)。

## `npm test` 在 macOS Sierra 上挂起或崩溃

如果你运行 `npm test` 后控制台在打印 `react-scripts test` 之后卡住,可能是你的 [Watchman](https://facebook.github.io/watchman/) 安装有问题,详见 [facebook/create-react-app#713](https://github.com/facebook/create-react-app/issues/713)。

建议先删除项目中的 `node_modules` 并重新运行 `npm install`(如果你用 yarn 就运行 `yarn`)。如果没解决,可以尝试这些 issue 中提到的各种变通办法:

- [facebook/jest#1767](https://github.com/facebook/jest/issues/1767)
- [facebook/watchman#358](https://github.com/facebook/watchman/issues/358)
- [ember-cli/ember-cli#6259](https://github.com/ember-cli/ember-cli/issues/6259)

有反馈称安装 4.7.0 或更新版本的 Watchman 可以解决问题。如果你用 [Homebrew](https://brew.sh/),可以运行以下命令更新:

```
watchman shutdown-server
brew update
brew reinstall watchman
```

其他[安装方式](https://facebook.github.io/watchman/docs/install.html#build-install)见 Watchman 文档页。

如果还是不行,试试运行 `launchctl unload -F ~/Library/LaunchAgents/com.github.facebook.watchman.plist`。

也有反馈说_卸载_ Watchman 反而解决了问题。所以如果别无他法,把它从系统里移除再试一次。

## `npm run build` 过早退出

有反馈称 `npm run build` 在内存有限且没有交换空间的机器上会失败,这在云环境中很常见。即使小项目,该命令也可能让系统内存占用增加数百 MB,所以如果你的可用内存不足 1 GB,构建很可能以以下消息失败:

> The build failed because the process exited too early. This probably means the system ran out of memory or someone called `kill -9` on the process.(构建失败,因为进程过早退出。这通常意味着系统内存耗尽,或有人对进程执行了 `kill -9`。)

如果你确定不是自己终止的进程,考虑给构建所在机器[增加一些交换空间](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04),或者改在本地构建。

## `npm run build` 在 Heroku 上失败

这可能是文件名大小写敏感的问题。请参阅[这一节](deployment.md#resolving-heroku-deployment-errors)。

## Moment.js 语言包缺失

如果你使用 [Moment.js](https://momentjs.com/),可能注意到默认只有英语语言包可用。这是因为语言包文件很大,而你很可能只需要 [Moment.js 提供的全部语言](https://momentjs.com/#multiple-locale-support)中的一小部分。

要把特定 Moment.js 语言包加进 bundle,需要显式引入它。

例如:

```js
import moment from 'moment';
import 'moment/locale/fr';
```

如果以这种方式引入了多个语言包,之后可以通过 `moment.locale()` 传入语言名来切换:

```js
import moment from 'moment';
import 'moment/locale/fr';
import 'moment/locale/es';

// ...

moment.locale('fr');
```

这只对之前显式引入过的语言包有效。

## `npm run build` 压缩失败

在 `react-scripts@2.0.0` 之前,这个问题由第三方 `node_modules` 使用现代 JavaScript 特性引起,因为压缩器无法在构建时处理它们。`react-scripts@2.0.0` 及更高版本已经通过编译 `node_modules` 内的标准现代 JavaScript 特性解决了这个问题。

如果你看到这个错误,说明你很可能在用旧版 `react-scripts`。可以避开使用现代语法的依赖来修复,或者升级到 `react-scripts@>=2.0.0` 并按变更日志中的迁移说明操作。
