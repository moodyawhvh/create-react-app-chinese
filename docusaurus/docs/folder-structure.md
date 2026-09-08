---
id: folder-structure
title: 目录结构
---

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

创建完成后,你的项目应该长这样:

```
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

要让项目成功构建,**这些文件必须以确切的文件名存在**:

- `public/index.html` 是页面模板;
- `src/index.js` 是 JavaScript 入口文件。

其他文件可以删除或重命名。

你可以在 `src` 里创建子目录。为了加快重新构建的速度,webpack 只处理 `src` 内的文件。你必须**把所有 JS 和 CSS 文件放进 `src`**,否则 webpack 看不到它们。

只有 `public` 内的文件才能被 `public/index.html` 引用。下面会介绍如何在 JavaScript 和 HTML 中使用资源文件。

不过,你可以创建更多顶层目录。它们不会被打进生产构建,所以可以用来放文档之类的内容。

如果你安装了 Git,并且你的项目不是一个更大仓库的一部分,则会初始化一个新仓库,产生一个额外的顶层 `.git` 目录。
