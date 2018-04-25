# node 随手小记
>顺便锻炼下markdown

## process.env.NODE_ENV
>项目中经常用到这个东西来区分`生产/开发`环境。比如react开发时用到的webpack打包
```
*package.json
"scripts": {
    "start": "webpack-dashboard -- webpack-dev-server",
    "build": "cross-env NODE_ENV=prod webpack --progress --profile",
}

*webpack.config.js
if (process.env.NODE_ENV === 'prod') {
  module.exports = require('./webpack.config.prod');
} else {
  module.exports = require('./webpack.config.dev');
}
```
>上面代码的作用，当执行 `npm start`时因为命令中没有传入`NODE_ENV`所以执行dev，反之执行`npm run build`执行prod。下面我们来看看`process`是个什么东西
### process
>官方解释：process 对象是一个 global （全局变量），提供有关信息，控制当前 Node.js 进程。作为一个对象，它对于 Node.js 应用程序始终是可用的，故无需使用 require()。[文档](http://nodejs.cn/api/process.html)
* process.env 官方: process.env属性返回一个包含用户环境信息的对象。[文档](http://nodejs.cn/api/process.html#process_process_env)
>这个属性可以返回用户所在运行环境的一些信息，`node`中常用的到的环境变量是`NODE_ENV`。上例中使用到了[cross-env](https://www.npmjs.com/package/cross-env)来保证`运行跨平台设置和使用环境变量`。在运行`npm run build`时设置变量`NODE_ENV=prod`

