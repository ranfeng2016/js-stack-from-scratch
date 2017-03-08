# 更新日志

## V2 (当前版本 v2.4.3)

- Gulp 任务流形式替换成 NPM (Yarn) scripts。
- 使用了Express, 对静态模版支持ES6的模版字符串解析. 开启了 Gzip 压缩加速。
- 在开发模式使用 Nodemon 自动重启开发模式、生产模式使用 PM2 服务稳定部署。
- 利用 Webpack 处理资源依赖和压缩文件。
- 使用 webpack-dev-server 开启服务本地开发，并支持模块热更新 (HMR) 和 `react-hot-loader`。
- 添加一个关于 `redux-thunk` 异步调用案例。
- 语法检查 / 类型检测 / 单元测试 不在是文件变动时触发，替换成 Git Hooks 事件监听。
- 有些章节已经结合起来，使得更容易维护教程。
- 单元测试由 Chai/Mocha 替换成 Jest。
- 添加路由 (React-Router), 服务端渲染 (SSR) 以及 `react-helmet`。
- 重命名 "Dog" 替换成 "hello"。
- 添加 Bootstrap (Twitter 开源), JSS, 和 `react-jss` 样式预处理器。
- 添加 Websocket 例子，使用的是 Socket.IO。
- 可选前端持续集成方案：Heroku, Travis, 和 Coveralls 代码测试覆盖率。
