---
id: adding-a-sass-stylesheet
title: 添加 Sass 样式表
sidebar_label: 添加 Sass 样式表
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

> 注意:此功能需要 `react-scripts@2.0.0` 及更高版本。

一般来说,我们不建议在不同组件间复用同一批 CSS 类。例如,与其在 `<AcceptButton>` 和 `<RejectButton>` 组件里共用一个 `.Button` CSS 类,我们更建议创建一个自带 `.Button` 样式的 `<Button>` 组件,让 `<AcceptButton>` 和 `<RejectButton>` 都去渲染它(而不是[继承](https://facebook.github.io/react/docs/composition-vs-inheritance.html))。

遵循这条规则后,CSS 预处理器往往就没那么有用了,因为 mixin 和嵌套之类的特性已被组件组合取代。不过,如果你觉得有价值,仍然可以集成 CSS 预处理器。

要使用 Sass,先安装 `sass`:

```sh
$ npm install sass
# 或者
$ yarn add sass
```

现在你可以把 `src/App.css` 重命名为 `src/App.scss`,并把 `src/App.js` 改为引入 `src/App.scss`。
任何文件只要以 `.scss` 或 `.sass` 扩展名引入,都会被自动编译。

要在多个 Sass 文件之间共享变量,可以使用 Sass 的 [`@use` 规则](https://sass-lang.com/documentation/at-rules/use)。例如,`src/App.scss` 和其他组件样式文件里可以写 `@use "./shared.scss";` 来引入变量定义。

这样就可以这样引入:

```scss
@use 'styles/_colors.scss'; // 假设 src/ 下有一个 styles 目录
@use '~nprogress/nprogress'; // 从 nprogress 这个 node 模块加载 css 文件
```

> **注意:** 如上所示,路径前加 `~` 前缀可以从 `node_modules` 解析模块。

`sass` 同样支持 `SASS_PATH` 变量。

要使用相对你指定路径的导入,可以在项目根目录添加一个 [.env 文件](https://github.com/facebook/create-react-app/blob/main/docusaurus/docs/adding-custom-environment-variables.md#adding-development-environment-variables-in-env),并在 `SASS_PATH` 环境变量中写明路径。要指定多个目录,用 `:` 分隔追加到 `SASS_PATH`,如 `path1:path2:path3`。

> **注意:** Windows 系统下请用分号分隔路径。
>
> ```
> SASS_PATH=path1;path2;path3
> ```

> **提示:** 这个功能也可以配合 [CSS Modules](adding-a-css-modules-stylesheet.md) 使用!

> **注意:** 如果你使用 Flow,请在 `.flowconfig` 中覆盖 [module.file_ext](https://flow.org/en/docs/config/options/#toc-module-file-ext-string) 设置,让它能识别 `.sass` 或 `.scss` 文件。同时还需要保留 `.js`、`.jsx`、`.mjs` 和 `.json` 文件的默认 `module.file_ext` 配置。
>
> ```
> [options]
> module.file_ext=.js
> module.file_ext=.jsx
> module.file_ext=.mjs
> module.file_ext=.json
> module.file_ext=.sass
> module.file_ext=.scss
> ```

> **注意:** LibSass 以及基于它的包(包括 Node Sass)已被[弃用](https://sass-lang.com/blog/libsass-is-deprecated)。
> 如果你是 Node Sass 用户,可以把 `package.json` 中的 `node-sass` 替换为 `sass`,或者运行以下命令迁移到 Dart Sass:
>
> ```sh
> $ npm uninstall node-sass
> $ npm install sass
> # 或者
> $ yarn remove node-sass
> $ yarn add sass
> ```
