# 网站(Website)

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

本网站基于 Docusaurus 2(一个现代化的静态网站生成器)构建。

### 安装

```
$ npm install
```

### 本地开发

```
$ npm start
```

该命令会启动本地开发服务器并打开浏览器窗口。绝大多数改动会实时生效,无需重启服务器。

### 构建

```
$ npm run build
```

该命令会把静态内容生成到 `build` 目录,可以使用任何静态内容托管服务来部署。

### 部署

```
$ GIT_USER=<你的 GitHub 用户名> USE_SSH=1 npm run deploy
```

如果你使用 GitHub Pages 托管,这条命令可以方便地构建网站并推送到 `gh-pages` 分支。
