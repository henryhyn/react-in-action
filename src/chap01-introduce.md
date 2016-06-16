# 快速上手

当下最热门的前端框架, 毫无疑问是 [React](https://facebook.github.io/react/index.html).
尤其是 Facebook 在 2016 年 4 月 7 日, 发布了 React v15.0,
直接从 v0.14.8 跳到 v15.0, 告诉开发者, React 已经不再是开发版, 而是可以用于实践的稳定版本, 这坚定了开发者的信心!

React 起源于 Facebook 的内部项目,
因为该公司对市场上所有 JavaScript MVC 框架, 都不满意, 就决定自己写一套,
用来架设 [Instagram](https://instagram.com) 网站.
做出来以后, 发现这套东西很好用, 就在 2013 年 5 月开源了.

![](images/bg2015033101.png)

由于 React 的设计思想极其独特, 属于革命性创新, 性能出众, 代码逻辑却非常简单.
所以, 越来越多的人开始关注和使用, 认为它可能是将来 Web 开发的主流工具.

React 项目本身也越滚越大, 从最早的 UI 引擎变成了一整套前后端通吃的 Web App 解决方案.
衍生的 [React Native](http://facebook.github.io/react-native/) 项目, 目标更是宏伟, 希望用写 Web App 的方式去写 Native App.
如果能够实现, 整个互联网行业都会被颠覆, 因为同一组人只需要写一次 UI , 就能同时运行在服务器、浏览器和手机.

![](images/bg2015031302.jpg)

既然 React 这么热门, 看上去充满希望, 当然应该好好学一下.
从技术角度, 可以满足好奇心, 提高技术水平;
从职业角度, 有利于求职和晋升, 有利于参与潜力大的项目.

## Hello world

按照程序界学习一门新技术的惯例, 写一个 Hello world 程序.
所需的 React 发布包, 可以到[官网](https://facebook.github.io/react/downloads.html)下载;
简单起见, 也可以使用公共 CDN 资源.
新建一个 `index.html` 文件, 内容如下

```{.numberLines}
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>React Demo</title>
    <script src="//cdn.bootcss.com/react/15.1.0/react.min.js"></script>
    <script src="//cdn.bootcss.com/react/15.1.0/react-dom.min.js"></script>
    <script src="//cdn.bootcss.com/babel-core/5.8.34/browser.min.js"></script>
</head>
<body>
<div id="container"></div>
<script type="text/babel">
    ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('container')
    );
</script>
</body>
</html>
```

上面是使用 React 的基本 HTML 模板, 代码有两个地方需要注意.
首先, 最后一个 `<script>` 标签的 `type` 属性为 `text/babel` .
这是因为 React 独有的 JSX 语法, 跟 JavaScript 不兼容.
凡是使用 JSX 的地方, 都要加上 `type="text/babel"` .

其次, 上面代码一共用了三个库:
`react.js` 、`react-dom.js` 和 `browser.js`, 它们必须首先加载.
其中, `react.js` 是 React 的核心库, `react-dom.js` 提供与 DOM 相关的功能,
`browser.js` 的作用是将 JSX 语法转为 JavaScript 语法, 这一步很消耗时间,
实际上线的时候, 应该预先编译打包好, 这部分知识将在第二章详细介绍.

`ReactDOM.render` 是 React 的最基本方法, 用于将模板转为 HTML 语言, 并插入指定的 DOM 节点.
上面代码将一个 `h1` 标题, 插入 `container` 节点.
由于使用了 CDN 资源, 需要将网页放在类似 Apache 的 Web 容器下, 然后用浏览器打开 <http://localhost/index.html>, 可以看到如下输出结果

![](images/demo01.png)

需要说明的是, React 不仅可以在浏览器运行, 还可以在服务器运行, 两者的用法差别不大.

## JSX 语法

上一节的代码,  HTML 语言直接写在 JavaScript 语言之中, 不加任何引号, 这就是 [JSX 的语法](http://facebook.github.io/react/docs/displaying-data.html#jsx-syntax), 它允许 HTML 与 JavaScript 的混写.

上面代码体现了 JSX 的基本语法规则:
遇到 HTML 标签 (以 `<` 开头), 就用 HTML 规则解析;
遇到代码块 (以 `{` 开头), 就用 JavaScript 规则解析.

JSX 允许直接在模板插入 JavaScript 变量.

## 参考文献

-   [React 入门实例教程](http://www.ruanyifeng.com/blog/2015/03/react.html)
