# 项目创建

## Node

### 简介

node 自带的 [npm](https://www.npmjs.com) 全称是 node package manager, 即 Node 包管理.
可用作 JS 模块依赖管理, 就连老牌的 JS 依赖管理工具 [Bower](https://bower.io),
都推荐使用 npm 来管理 node 模块之间的依赖关系.

### 安装 Node

进入 NodeJS [官方网站](https://nodejs.org/en/),
截止目前为止, 最新版为 `v4.4.5`, 根据电脑系统下载对应的版本.
双击下载文件, 根据提示完成安装.
在命令行中, 检查 node 和 npm 的版本.

```{.bash .numberLines}
$ node -v
v4.4.5
$ npm -v
2.15.5
```

在接下来的项目创建中, 将用 npm 安装相关的依赖包.
在国内由于某些原因, 下载速度相当慢, 可以参照如下方法,
配置国内代理, 在用户 Home 目录创建 `.npmrc` 文件, 写入如下内容,
以后使用 `npm install` 命令就相当于从 taobao 源下载.
详情参见[这里](https://npm.taobao.org).

```{.numberLines}
registry=https://registry.npm.taobao.org/
```

### 初始化项目

创建项目 `react-webpack-demo`.

```{.bash .numberLines}
mkdir react-webpack-demo
cd react-webpack-demo
npm init
# 如果懒得填一些信息, 一直点回车即可
```

如果你使用 git 管理你的这个项目的话, 建议你新建一个 `.gitignore` 文件, 不要让 git 提交一些 node 依赖的模块,
简单起见, 就写入如下内容.

```{.numberLines}
.idea
node_modules
npm-debug.log
```

如果有 GitHub 账号, 建议将项目 push 到线上仓库, 一来有利于分享, 二来防止文件丢失.
本项目的代码可以在[这里](https://github.com/henryhyn/react-webpack-demo)找到.

### 创建主文件

新建文件 `app/index.js`, 作为项目的入口, 写入以下内容

```{.numberLines}
document.write('<h1>Hello, world!</h1>');
```

## Webpack

### 简介

官网对 webpack 的定义是 MODULE BUNDLER, 他的目的就是把有依赖关系的各种文件打包成一系列的静态资源.
请看下图

![](55fb7d622403852ff7533c6da5c620cd_r.png)

webpack 简单点来说就就是一个配置文件, 所有的魔力都是在这一个文件中发生的.
这个配置文件主要分为三大块

-   entry 入口文件. 让 webpack 用哪个文件作为项目的入口
-   output 出口. 让 webpack 把处理完成的文件放在哪里
-   module 模块. 要用什么不同的模块来处理各种类型的文件

### 安装 webpack

因为 webpack 是一个基于 node 的项目, 所以要按照上一节预先装好 node 和 npm, 然后执行如下命令

```{.bash .numberLines}
$ npm install -g webpack
```

### 配置 Webpack

先安装两个插件

```{.bash .numberLines}
$ npm install html-webpack-plugin webpack-dev-server --save-dev
```

然后, 在项目目录下, 创建 `webpack.config.js` 配置文件, 内容如下.

```{.numberLines}
var path = require('path');
var HtmlwebpackPlugin = require('html-webpack-plugin');
var ROOT_PATH = path.resolve(__dirname);
var APP_PATH = path.resolve(ROOT_PATH, 'app');
var BUILD_PATH = path.resolve(ROOT_PATH, 'build');
module.exports = {
    entry: APP_PATH,
    output: {
        path: BUILD_PATH,
        filename: 'bundle.js'
    },
    devServer: {
        historyApiFallback: true,
        hot: true,
        inline: true,
        progress: true
    },
    plugins: [
        new HtmlwebpackPlugin({
            title: 'React Demo'
        })
    ]
};
```

完成配置以后, 在项目目录下, 运行如下命令, 即可启动服务.

```{.bash .numberLines}
$ webpack-dev-server --hot --inline
```

用浏览器打开 <http://localhost:8080> 即可看到运行效果.
上面的 `--hot` 参数是的 JS 文件有改动时, 自动加载, 并且浏览器自动刷新,
这种开发体验是不是很好, 赶快改动试试看吧!

如果每次启动服务, 都要写这么长一段命令, 可能很难记住,
幸好 npm 支持"钩子机制"的配置, 在 `package.json` 的 `scripts` 模块,
增加 `prestart` 和 `start` 两个功能支持.

```{.numberLines}
"scripts": {
  "prestart": "npm install",
  "start": "webpack-dev-server --hot --inline --port 9999",
  "test": "echo \"Error: no test specified\" && exit 1"
}
```

以后, 我们在项目目录下, 执行 `npm start` 即可启动项目, 并且会预先检查所需模块是否安装完毕,
这样的好处是, 协同开发, 或打开一个新项目时, 你只需要告诉他用 `npm start` 命令即可.
此外, 这里把端口号改成了 9999, 因为 8080 一般是 Java Tomcat 的端口号, 将来做后端服务开发时, 可能会用到.

## React

## 安装 React

终于到了本书主角上场了, 本小节为项目添加 React 支持,
在项目目录下, 运行如下安装命令.

```{.bash .numberLines}
npm install react react-dom --save
npm install babel-loader babel-core --save-dev
npm install babel-preset-es2015 babel-preset-react --save-dev
```

### 配置 Loader

在 `webpack.config.js` 中加入 `module` 配置, 这里仅加入 ``

```{.numberLines}
module: {
    loaders: [{
        test: /\.js$/,
        include: APP_PATH,
        loader: 'babel',
        query: {
            presets: ['react', 'es2015']
        }
    }]
},
```

### 配置模板

## Webpack 高级功能

### 构建打包

### 样式分离

## 参考文献

-   [Webpack傻瓜式指南（一）](https://zhuanlan.zhihu.com/p/20367175)
-   [Webpack傻瓜指南（二）开发和部署技巧](https://zhuanlan.zhihu.com/p/20397902)
-   [Webpack傻瓜指南（三）和React配合开发](https://zhuanlan.zhihu.com/p/20522487)