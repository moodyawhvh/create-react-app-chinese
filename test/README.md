# Create React App 端到端测试(E2E Tests)

> 🌐 本文档由 [react/create-react-app](https://github.com/react/create-react-app) 翻译,英文原版见原项目。

## 用法

这些测试确保各种功能契约在依赖升级后依然成立。

在本地开始:运行 `npx jest test/ --watchAll`。

建议过滤测试范围,避免每次全部重跑。最常见的测试是 webpack 报错信息相关的用例。<br>
只想跑 webpack 消息相关测试时,输入 `p`,再输入 `webpack-message`,按 `[enter]`。

## 它们是怎么工作的?

### `fixtures/`

每个 `fixture/` 都会在临时目录中启动,并使用 Yarn PnP 安装依赖(为了速度)。<br>
想退出 PnP,在对应 fixture 目录里创建一个 `.disable-pnp` 文件即可。

会创建一个全局对象(`testSetup`),它有几个有用的属性:

- `testSetup.testDirectory`:包含测试应用的目录
- `testSetup.scripts`:一个对象,允许你调用 `react-scripts` 及相关命令

然后运行该 `fixture/` 的全部测试。

#### `testSetup.scripts`

##### `start`

运行 `start` 命令,可以异步运行;传入 `{ smoke: true }` 时则以阻塞方式运行。<br>
异步运行时,它会返回 `port` 和一个用于清理进程的 `done` 函数。
阻塞运行时,它返回进程的 `stdout` 和 `stderr`。

##### `build`

运行 `build` 命令,返回进程的 `stdout` 和 `stderr`。

##### `test`

运行 `test` 命令,返回进程的 `stdout` 和 `stderr`。

##### `serve`

运行并伺服该应用。
它返回 `port` 和一个用于清理进程的 `done` 函数。
