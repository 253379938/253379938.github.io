---
title: webpack
date: 2024-12-08 21:08:13
categories:
  - 模块化
tags:
  - 模块化
---

<h1 id="ztgII">前言</h1>

<font style="color:rgb(53, 53, 53);">从Webpack开始的前端工程化探索</font>

<h1 id="dCQEd">模块化</h1>

<font style="color:rgb(53, 53, 53);">随着前端应用的日益复杂，程序员需要更高效的代码组织形式，以便提高可维护性并提升开发效率。</font>

<font style="color:rgb(53, 53, 53);">模块化将复杂的代码按功能的不同，分为不同的模块，单独维护，提高开发效率。</font>

**<font style="color:rgb(53, 53, 53);">模块：</font>**

1. <font style="color:rgb(53, 53, 53);">将一个复杂的程序依据一定的规则(规范)封装成几个块(文件), 并进行组合在一起。</font>
2. <font style="color:rgb(53, 53, 53);">块的内部数据与实现是私有的, 只是向外部暴露一些接口(方法)与外部其它模块通信。</font>

<h2 id="ZNsRX">演变</h2>

**<font style="color:rgb(53, 53, 53);">1、文件划分</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">将不同的功能及其状态数据存放在单独的JS文件中。约定一个文件就是一个模块，以单独的script标签引入至HTML。</font>

<font style="color:rgb(53, 53, 53);">虽然实现了功能的划分，但缺点也十分明显：</font>

1. <font style="color:rgb(53, 53, 53);">污染全局作用域</font>
2. <font style="color:rgb(53, 53, 53);">命名冲突</font>
3. <font style="color:rgb(53, 53, 53);">无法管理模块的依赖关系</font>

**<font style="color:rgb(53, 53, 53);">2、命名空间</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">在文件划分的基础上，约定每个模块只暴露一个全局的对象，对象包裹着模块的方法和状态。</font>

<font style="color:rgb(53, 53, 53);">虽然避免了命名冲突，但仍然没有私有空间，</font>

**<font style="color:rgb(53, 53, 53);">3、IIFE</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">通过立即执行函数实现私有空间，使用window暴露模块的成员，通过参数声明依赖。</font>

**js**

<font style="color:rgb(53, 53, 53);">在没有工具和相关规范的早期，以约定的形式，实践模块化思想的方式。</font>

<font style="color:rgb(53, 53, 53);">仍然存在问题：</font>

1. <font style="color:rgb(53, 53, 53);">依赖管理混乱</font>
2. <font style="color:rgb(53, 53, 53);">不同开发者、不同项目，模块化的实现有差异</font>
3. <font style="color:rgb(53, 53, 53);">模块的导入不受代码控制</font>

<h3 id="FjzOd">现代化</h3>

1. **<font style="color:rgb(53, 53, 53);">模块化规范：</font>**<font style="color:rgb(53, 53, 53);">对模块代码书写格式和交互规则的详细描述</font>
2. **<font style="color:rgb(53, 53, 53);">模块加载器：</font>**<font style="color:rgb(53, 53, 53);">使用代码的方式，自动控制模块的导入，管理模块的依赖。</font>

<font style="color:rgb(53, 53, 53);">在ES6模块化出现之前，为了解决模块化的需求，出现了众多的模块化机制，CommonJS(NodeJS内置)、AMD(require.js)、CMD(Sea.js)</font>

<font style="color:rgb(53, 53, 53);">ES6模块化出现后的</font>**<font style="color:rgb(53, 53, 53);">最佳实践</font>**<font style="color:rgb(53, 53, 53);">：</font>

1. <font style="color:rgb(53, 53, 53);">浏览器环境：ES Module</font>
2. <font style="color:rgb(53, 53, 53);">Node环境：CommonJS</font>

<h2 id="gt4Tx">ES Module</h2>

<font style="color:rgb(53, 53, 53);">ES6 模块的设计思想是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量，而 CommonJS 和 AMD 模块，都是运行时的</font>

```plain
<script type='module'>
  import { name } from './modules/index.js';
  export name;
</script>
```

<font style="color:rgb(53, 53, 53);">特性：</font>

1. <font style="color:rgb(53, 53, 53);">自动采用严格模式，忽略’use strict’</font>
2. <font style="color:rgb(53, 53, 53);">每个ESM模块都是单独的私有作用域</font>
3. <font style="color:rgb(53, 53, 53);">ESM通过CORS请求外部JS模块</font>
4. <font style="color:rgb(53, 53, 53);">ESM的script标签会延迟执行脚本(相当于defer)</font>

<font style="color:rgb(53, 53, 53);">详见</font>[<font style="color:rgb(53, 53, 53);">ES6查缺补漏 #Module模块化</font>](https://www.qcqx.cn/article/383b041f.html#Module%E6%A8%A1%E5%9D%97%E5%8C%96)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">MDN-JavaScript模块</font>](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Modules)

<h3 id="aTsbD">兼容性问题</h3>

<font style="color:rgb(53, 53, 53);">ES6仍然有兼容性问题，早期的浏览器，特别是国产和手机上的浏览器</font>

**shell**

使用 caniuse-cmd 检查兼容性

```plain
npm install -g caniuse-cmd
caniuse import
```

<font style="color:rgb(53, 53, 53);">可以引入</font><font style="color:rgb(53, 53, 53);"> </font>[<font style="color:rgb(53, 53, 53);">Polyfill</font>](https://polyfill.io/)<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">兼容</font>

<font style="color:rgb(53, 53, 53);">使用 webpack、vite 后，有更多的兼容插件可以安装使用，如</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">@vitejs/plugin-legacy</font>`

<font style="color:rgb(53, 53, 53);">script添加nomodule属性，仅在不支持ESM的浏览器上执行该脚本</font>

<h3 id="tWXEu">ESM in Node</h3>

<font style="color:rgb(53, 53, 53);">ESM在Node.js的v8.5.0中作为实验性功能被引入，v12.17.0为所有Node.js应用程序提供了ESM支持</font>

<font style="color:rgb(53, 53, 53);">使用</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">.mjs</font>`<font style="color:rgb(53, 53, 53);">、</font>`<font style="color:rgb(233, 105, 0);">.cjs</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">文件后缀区分 ESM 和 CommonJS 模块</font>

<font style="color:rgb(53, 53, 53);">原生Node环境中的ESM与CommonJS：</font>

1. <font style="color:rgb(53, 53, 53);">ES Module中可以导入CommonJS模块</font>
2. <font style="color:rgb(53, 53, 53);">CommonJS中不能导入ES Module模块</font>
3. <font style="color:rgb(53, 53, 53);">CommonJS始终只会导出一个默认成员</font>

<font style="color:rgb(53, 53, 53);">ESM得到CommonJS全局成员的值：</font>

```plain
// console.log(__dirname)
// ReferenceError: __dirname is not defined in ES module scope
import { fileURLToPath } from 'url'
import { dirname } from 'path'
const __filename = fileURLToPath(import.meta.url)
const __dirname = dirname(__filename)
console.log(__filename)
console.log(__dirname)
// c:\***\esm-in-node\index.mjs
// c:\***\esm-in-node
```

<h2 id="y8o51">前端打包工具</h2>

<font style="color:rgb(53, 53, 53);">ESM仍然存在一些问题：</font>

1. <font style="color:rgb(53, 53, 53);">存在兼容性问题</font>
2. <font style="color:rgb(53, 53, 53);">模块文件过多，网络请求频繁</font>
3. <font style="color:rgb(53, 53, 53);">不仅是JS，前端所有的资源，包括CSS、HTML都需要模块化</font>

<font style="color:rgb(53, 53, 53);">前端需要更好的工具和规范，让开发者继续享受模块化带来的便利，而不需要担心对</font>**<font style="color:rgb(53, 53, 53);">生产环境</font>**<font style="color:rgb(53, 53, 53);">产生的影响。</font>

**<font style="color:rgb(53, 53, 53);">需求推动技术的进步</font>**<font style="color:rgb(53, 53, 53);">，打包工具顺势出现了。打包工具解决的是前端整体的模块化，不只是局限于JS的模块化。</font>

<font style="color:rgb(53, 53, 53);">如今前端项目的代码组织，已经走上了</font>**<font style="color:rgb(53, 53, 53);">编辑代码</font>**<font style="color:rgb(53, 53, 53);">和</font>**<font style="color:rgb(53, 53, 53);">最终运行文件</font>**<font style="color:rgb(53, 53, 53);">完全两样的形式，一系列</font>**<font style="color:rgb(53, 53, 53);">工具链</font>**<font style="color:rgb(53, 53, 53);">和自动化的思想也融入进了打包工具中，打包也逐渐从一个技术问题，转变为了生态和管理问题。打包工具现在也可称为</font>**<font style="color:rgb(53, 53, 53);">构建工具</font>**<font style="color:rgb(53, 53, 53);">，支撑着前端工程化。</font>

<font style="color:rgb(53, 53, 53);">常见的打包工具：</font>[<font style="color:rgb(53, 53, 53);">Webpack</font>](https://webpack.docschina.org/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">Vite</font>](https://vitejs.dev/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">Rollup</font>](https://rollupjs.org/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">esbuild</font>](https://esbuild.github.io/)

<h1 id="uHXZM">Webpack</h1>

[<font style="color:rgb(53, 53, 53);">Webpack</font>](https://webpack.docschina.org/)<font style="color:rgb(53, 53, 53);">是一个用于现代 JavaScript 应用程序的静态模块打包工具。</font>

<font style="color:rgb(53, 53, 53);">学习webpack大体上就是学习webpack.config.js的配置、各种loaders和plugins的使用，所以，多看文档，广泛了解，取所需使用</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/concepts/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">配置</font>](https://webpack.docschina.org/configuration/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">指南</font>](https://webpack.docschina.org/guides/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">loaders</font>](https://webpack.docschina.org/loaders/)<font style="color:rgb(53, 53, 53);">、</font>[<font style="color:rgb(53, 53, 53);">plugins</font>](https://webpack.docschina.org/plugins/)

<h2 id="yrYsD">快速上手</h2>

```plain
npm init -y
npm install webpack webpack-cli --save-dev
```

```plain
{
  "private": true, // 防止意外发布
  "scripts": {
    "build": "webpack" // 打包命令
  },
}
```

<font style="color:rgb(53, 53, 53);">创建index.html和src目录，并写两个模块化文件：</font>

```plain
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <script type="module" src="src/index.js"></script>
</body>
</html>
```

```plain
import { createTitle } from "./module.js";
document.body.append(createTitle('Hello World'));
```

```plain
export const createTitle = (title) => {
  const element = document.createElement('h2')
  element.textContent = title
  element.addEventListener('click', () => {
    alert(title)
  })
  return element
}
```

<font style="color:rgb(53, 53, 53);">直接打开 index.html 可以看到页面上的 Hello World</font>

<font style="color:rgb(53, 53, 53);">接着使用webpack进行打包</font>

```plain
npx webpack
# 或
npm run build
```

<font style="color:rgb(53, 53, 53);">webpack自动创建了 dist 目录，存放了打包好的 main.js</font>

```plain
<!-- <script type="module" src="src/index.js"></script> -->
<!-- 打包好的main.js已经是ES5语法，可以去掉type="module" -->
<script src="dist/main.js"></script>
```

<font style="color:rgb(53, 53, 53);">打开 index.html 仍然可以看到 Hello World</font>

<font style="color:rgb(53, 53, 53);">Webpack4以后，支持这样0配置的方式，快速打包项目，src是默认打包入口，dist是输出，index.js -> main.js</font>

<h1 id="E4MOi">配置</h1>

<font style="color:rgb(53, 53, 53);">根目录的</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">webpack.config.js</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">是webpack默认的配置文件</font>

<font style="color:rgb(53, 53, 53);">可以手动创建配置文件，或在 VSCode 中下载</font>[<font style="color:rgb(53, 53, 53);">webpack插件</font>](https://marketplace.visualstudio.com/items?itemName=jeremyrajan.webpack)<font style="color:rgb(53, 53, 53);">，通过</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">Webpack Create</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">命令，初始化 webpack</font>

**默认创建的wbpack.config.js**

```plain
const path = require('path');
module.exports = {
  // 设置模式为开发模式
  mode: 'development',
  // 应用程序的入口点
  entry: path.join(__dirname, 'src', 'index'),
  // 启用监视模式，以在文件更改时进行自动重新编译
  watch: true,
  // 输出配置
  output: {
    // 存储输出文件的目录
    path: path.join(__dirname, 'dist'),
    // 打包文件的公共路径（由浏览器用于加载资源）
    publicPath: '/dist/',
    // 主要包的输出文件名
    filename: "bundle.js",
    // 动态加载的代码的输出文件名（代码分割）
    chunkFilename: '[name].js'
  },
  // 用于处理不同文件类型的模块配置
  module: {
    // 使用Babel处理JavaScript和JSX文件的规则
    rules: [{
      // 用于匹配以.jsx或.js结尾的文件
      test: /.jsx?$/,
      // 只处理src目录下的文件
      include: [
        path.resolve(__dirname, 'src')
      ],
      // 排除node_modules目录下的文件
      exclude: [
        path.resolve(__dirname, 'node_modules')
      ],
      // 使用babel-loader进行转译
      loader: 'babel-loader',
      options: {
        // 使用指定的Babel预设
        presets: [
          ["@babel/env", {
            // 指定目标浏览器版本为最近的两个Chrome版本
            "targets": {
              "browsers": "last 2 chrome versions"
            }
          }]
        ]
      }
    }]
  },
  // 配置模块解析的文件扩展名
  resolve: {
    extensions: ['.json', '.js', '.jsx']
  },
  // 生成源映射以方便调试
  devtool: 'source-map',
  // 配置开发服务器
  devServer: {
    // 提供内容的基本目录
    contentBase: path.join(__dirname, '/dist/'),
    // 启用内联模式，自动注入脚本以处理实时更新
    inline: true,
    // 服务器主机
    host: 'localhost',
    // 服务器端口
    port: 8080,
  }
};
```

<font style="color:rgb(53, 53, 53);">JS配置文件运行在node环境中，所以需要使用CommonJS写法</font>

<font style="color:rgb(53, 53, 53);">插件还会自动安装这些插件：</font>

```plain
"devDependencies": {
  "webpack": "^5.74.0",
  "webpack-cli": "^4.10.0",
  "@babel/core": "^7.18.13",
  "@babel/preset-env": "^7.18.10",
  "babel-loader": "^8.2.5",
  "webpack-dev-server": "^4.10.0"
}
```

<h2 id="GATLr">基本概念</h2>

1. `<font style="color:rgb(233, 105, 0);">entry</font>`<font style="color:rgb(53, 53, 53);">: webpack打包的入口起点，从这里开始根据各个文件之间的依赖来对文件进行打包。单页面应用只有一个入口起点，多页面应用则存在多个入口起点</font>
2. `<font style="color:rgb(233, 105, 0);">output</font>`<font style="color:rgb(53, 53, 53);">: 打包文件输出定义的地方，定义打包后输出文件的名字以及输出路径等</font>
3. `<font style="color:rgb(233, 105, 0);">mode</font>`<font style="color:rgb(53, 53, 53);">: 模式，webpack打包的模式，分为三种 development、production、none</font>
4. `<font style="color:rgb(233, 105, 0);">loader</font>`<font style="color:rgb(53, 53, 53);">: 对javascript等文件进行预处理的，可以通过loader来构建包含javascript在内的任何静态资源</font>
5. `<font style="color:rgb(233, 105, 0);">plugin</font>`<font style="color:rgb(53, 53, 53);">: 插件是用来解决loader解决不了的问题，它可以在webpack构建过程中任何一个节点来调用</font>

[<font style="color:rgb(53, 53, 53);">createapp.dev</font>](https://createapp.dev/webpack/)<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">是一个创建自定义 webpack 配置的在线工具</font>

<font style="color:rgb(53, 53, 53);">使用不同的配置文件：</font>

```plain
"scripts": {
  "build": "webpack --config prod.config.js"
}
```

<h1 id="oPcrk">入口和上下文</h1>

<font style="color:rgb(53, 53, 53);">入口对象是用于 webpack 查找开始构建 bundle 的地方。上下文是入口文件所处的目录的绝对路径的字符串。</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/configuration/entry-context/)

<h2 id="Gw0xq">基础目录context</h2>

`<font style="color:rgb(233, 105, 0);">context</font>`<font style="color:rgb(53, 53, 53);"> 基础目录，</font>**<font style="color:rgb(53, 53, 53);">绝对路径</font>**<font style="color:rgb(53, 53, 53);">，解析入口点(entry point)和加载器(loader)</font>

```plain
context: path.resolve(__dirname, 'src'),
```

<font style="color:rgb(53, 53, 53);">配置了context后，entry路径相对于context</font>

```plain
entry: './src/index.js',
// 配置context后
context: path.resolve(__dirname, 'src'),
entry: './index.js',
```

<h2 id="G263V">入口entry</h2>

<font style="color:rgb(53, 53, 53);">entry指示webpack使用一个或多个模块，来作为构建应用的入口，webpack会找出哪些模块和是入口起点的直接或者间接的依赖，并将其打包到一起。默认值</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">./src/index.js</font>`

**<font style="color:rgb(53, 53, 53);">value类型：</font>**<font style="color:rgb(53, 53, 53);">string、array、object</font>

<font style="color:rgb(53, 53, 53);">入口分为</font>**<font style="color:rgb(53, 53, 53);">单入口</font>**<font style="color:rgb(53, 53, 53);">(单页应用SPA)和</font>**<font style="color:rgb(53, 53, 53);">多入口</font>**<font style="color:rgb(53, 53, 53);">(多页面应用)</font>

**<font style="color:rgb(53, 53, 53);">1、单入口</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">单入口主要使用string、array为值，应用于单页应用SPA</font>

```plain
entry: './index.js',
// 将这两个文件以及其中所依赖的代码打包到同一个文件中
entry: ['./index.js', './main.js'],
```

<font style="color:rgb(53, 53, 53);">这种写法默认的chunkname是main，是object的简略写法</font>

object完整写法

```plain
entry: {
  main: './index.js',
},
entry: {
  main: ['./index.js', './main.js'],
},
```

**<font style="color:rgb(53, 53, 53);">2、多入口</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">多入口即有多个html，分别需要不同的打包好的js</font>

```plain
{
  entry: {
    main: './src/main.js',
    bundle: './src/index.js'
  },
  // 这里的[name]相当于是个占位符，值就是上面入口的key值，单入口时可以写死，不过不建议
  output: {
    // 多入口需要对应多出口，通常用[name]占位，不然打包会报错
    filename: '[name].js'
  }
}
```

<font style="color:rgb(53, 53, 53);">可以看到dist目录下打包好了 main.js 和 index.js 两个文件</font>

**<font style="color:rgb(53, 53, 53);">3、更多配置</font>**<font style="color:rgb(53, 53, 53);">  
</font><font style="color:rgb(53, 53, 53);">打包入口不仅仅是写一个入口文件地址就可以，它还有额外的配置：</font>

1. `<font style="color:rgb(233, 105, 0);">dependOn</font>`<font style="color:rgb(53, 53, 53);">: 指当前入口文件所依赖的模块，这些模块必须在入口文件被加载前加载</font>
2. `<font style="color:rgb(233, 105, 0);">filename</font>`<font style="color:rgb(53, 53, 53);">: 指定要输出的文件名称(优先级高于output中的filename和path)</font>
3. `<font style="color:rgb(233, 105, 0);">import</font>`<font style="color:rgb(53, 53, 53);">: 启动时要加载的模块(入口文件地址)</font>

```plain
{
  entry: {
    index: './index.js',
    main: './main.js',
    catalog: {
      import: './catalog.js',
      filename: 'pages/log.js',
      dependOn: 'main',
    },
  },
  output: {
    filename: '[name].js',
  }
}
```

<h2 id="LjQ58">出口output</h2>

<font style="color:rgb(53, 53, 53);">output配置的作用是告知webpack如何向硬盘写入打包好的文件。</font>

**<font style="color:rgb(53, 53, 53);">注意：</font>**<font style="color:rgb(53, 53, 53);">entry可以存在多个入口，但output只有一个出口配置</font>

**<font style="color:rgb(53, 53, 53);">配置项：</font>**

1. <font style="color:rgb(53, 53, 53);">filename 打包文件名，默认main.js</font>
2. <font style="color:rgb(53, 53, 53);">path 打包文件输出路径，默认dist</font>
3. <font style="color:rgb(53, 53, 53);">clean 输出包前清空输出目录，默认false</font>

**<font style="color:rgb(53, 53, 53);">1、filename</font>**

```plain
// [name]对应entry的key
output: {
  filename: '[name].js',
}
// 使用内部chunk id占位
output: {
  filename: '[id].bundle.js',
  // main-0.js
},
// 使用由生成的内容产生的 hash，通常和[name]组合使用
output: {
  filename: '[name]-[contenthash].js',
  // main-8bc05850732530fe321c.js
},
```

**<font style="color:rgb(53, 53, 53);">2、path 和 clean</font>**

```plain
output: {
  path: path.resolve(__dirname, 'dist'),
  filename: '[name]-[contenthash].js',
  clean: true,
}
```

<h1 id="pVq9O">工作模式mode</h1>

`<font style="color:rgb(233, 105, 0);">mode</font>`<font style="color:rgb(53, 53, 53);"> 用于设置webpack的工作模式，告知 webpack 使用相应模式的内置优化</font>

```plain
module.exports = {
  mode: 'development',
};
```

<font style="color:rgb(53, 53, 53);">三种工作模式：</font>

1. **<font style="color:rgb(53, 53, 53);">production</font>**<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">默认，生产模式，启用自动压缩代码、去除业务无关代码等</font>
2. **<font style="color:rgb(53, 53, 53);">development</font>**<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">开发模式</font>
3. **<font style="color:rgb(53, 53, 53);">none</font>**<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">不使用任何默认优化选项</font>

<h1 id="yAZpM">打包结果分析</h1>

<font style="color:rgb(53, 53, 53);">将 mode 设为 none，查看输出文件</font>

```plain
/******/ (() => { // webpackBootstrap
/******/ 	"use strict";
/******/ 	var __webpack_modules__ = ([
/******/ 	]);
/************************************************************************/
/******/ 	// The module cache
/******/ 	var __webpack_module_cache__ = {};
/******/ 	
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/ 	}
/******/ 	
/************************************************************************/
/******/ 	/* webpack/runtime/define property getters */
/******/ 	(() => {
/******/ 	})();
/******/ 	
/******/ 	/* webpack/runtime/hasOwnProperty shorthand */
/******/ 	(() => {
/******/ 	})();
/******/ 	
/******/ 	/* webpack/runtime/make namespace object */
/******/ 	(() => {
/******/ 	})();
/******/ 	
/************************************************************************/
var __webpack_exports__ = {};
// This entry need to be wrapped in an IIFE because it need to be isolated against other entry modules.
(() => {
})();

// This entry need to be wrapped in an IIFE because it need to be isolated against other entry modules.
(() => {
})();

/******/ })()
;
```

<font style="color:rgb(53, 53, 53);">先看最末尾的两个IIFE，两个入口文件 index.js 和 main.js，分别被打包为了立即执行函数，以此实现私有作用域</font>

<h1 id="WlqMk">loader</h1>

[<font style="color:rgb(53, 53, 53);">loader</font>](https://webpack.docschina.org/concepts/loaders/)<font style="color:rgb(53, 53, 53);">是webpack实现前端模块化的核心，用于将指定格式的资源文件按一定格式进行转换输出</font>

<font style="color:rgb(53, 53, 53);">例如，可以使用 loader 告诉 webpack 加载 CSS 文件，或者将 TypeScript 转为 JavaScript。</font>

<font style="color:rgb(53, 53, 53);">官方:</font>[<font style="color:#117CEE;">Loaders | webpack 中文文档</font>](https://webpack.docschina.org/loaders/)

**<font style="color:rgb(53, 53, 53);">特点：</font>**

1. <font style="color:rgb(53, 53, 53);">单一职责：一个Loader只做一件事情，正因为职责越单一，所以Loaders的组合性强，可配置性好</font>
2. <font style="color:rgb(53, 53, 53);">loader支持链式调用，上一个loader的处理结果可以传给下一个loader接着处理，上一个Loader的参数options可以传递给下一个loader，直到最后一个loader，返回Webpack所期望的JavaScript</font>

<font style="color:rgb(53, 53, 53);">webpack内部的default loader只能处理JavaScript，想要处理如css、ts等其它类型文件，就要安装对应的loader</font>

<font style="color:rgb(53, 53, 53);">loader可以分为三类：</font>

1. <font style="color:rgb(53, 53, 53);">编译转换型：如css-loader</font>
2. <font style="color:rgb(53, 53, 53);">文件操作型：如file-loader</font>
3. <font style="color:rgb(53, 53, 53);">代码检查型：如eslint-loader</font>

**<font style="color:rgb(53, 53, 53);">案例：</font>**

```javascript
// 用于处理不同文件类型的模块配置
module: {
  // 使用Babel处理JavaScript和JSX文件的规则
  rules: [{
    // 用于匹配以.jsx或.js结尾的文件
    test: /.jsx?$/,
    // 只处理src目录下的文件
    include: [
      path.resolve(__dirname, 'src')
    ],
    // 排除node_modules目录下的文件
    exclude: [
      path.resolve(__dirname, 'node_modules')
    ],
    // 使用babel-loader进行转译
    loader: 'babel-loader',
    options: {
      // 使用指定的Babel预设
      presets: [
        ["@babel/env", {
          // 指定目标浏览器版本为最近的两个Chrome版本
          "targets": {
            "browsers": "last 2 chrome versions"
          }
        }]
      ]
    }
  }]
},
```

<font style="color:rgb(53, 53, 53);">Module的文档：</font>[<font style="color:#117CEE;">Module | webpack 中文文档</font>](https://webpack.docschina.org/configuration/module/)

<h2 id="ijkvD">加载css</h2>

<font style="color:rgb(53, 53, 53);">查看官方文档</font>[<font style="color:rgb(53, 53, 53);">指南-管理资源-加载CSS</font>](https://webpack.docschina.org/guides/asset-management/#loading-css)

<font style="color:rgb(53, 53, 53);">安装所需的loader</font>

```plain
npm install --save-dev style-loader css-loader
```

<font style="color:rgb(53, 53, 53);">添加配置，</font>[<font style="color:rgb(53, 53, 53);">css-loader</font>](https://webpack.docschina.org/loaders/css-loader/)<font style="color:rgb(53, 53, 53);">将css文件打包为js模块，</font>[<font style="color:rgb(53, 53, 53);">style-loader</font>](https://webpack.docschina.org/loaders/style-loader/)<font style="color:rgb(53, 53, 53);">把 CSS 插入到 DOM 中（css-loader将css push到一个数组中，style-loader将数组中的css通过style标签追加到html-head中）</font>

```plain
module.exports = {
  module: {
    rules: [
      {
        // 正则匹配loader要处理的资源
        test: /\.css$/i,
        // 逆序执行，从右往左
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
}
```

<font style="color:rgb(53, 53, 53);">src目录下创建index.css,打包入口中使用该css</font>

```plain
import './index.css'
```

<font style="color:rgb(53, 53, 53);">现在样式已经生效</font>

<font style="color:rgb(53, 53, 53);">webpack推荐我们使用import根据JS代码的需要</font>**<font style="color:rgb(53, 53, 53);">动态</font>**<font style="color:rgb(53, 53, 53);">导入资源，就像刚刚import css一样，这样的代码与资源的关系，更符合模块化的依赖思想</font>

<h2 id="ampB3">加载其它资源</h2>

<font style="color:rgb(53, 53, 53);">webpack5使用</font>[<font style="color:#117CEE;">资源模块Asset Modules</font>](https://webpack.docschina.org/guides/asset-modules/)<font style="color:rgb(53, 53, 53);">来加载图片、字体等资源，webpack4则使用</font>[<font style="color:rgb(53, 53, 53);">file-loader</font>](https://v4.webpack.docschina.org/loaders/file-loader/)<font style="color:rgb(53, 53, 53);">和</font>[<font style="color:rgb(53, 53, 53);">url-loader</font>](https://v4.webpack.docschina.org/loaders/url-loader/)<font style="color:rgb(53, 53, 53);">等</font>

<h3 id="OBn90">file-loader</h3>

<font style="color:rgb(53, 53, 53);">安装</font>[<font style="color:#117CEE;">file-loader</font>](https://v4.webpack.docschina.org/loaders/file-loader/)<font style="color:rgb(53, 53, 53);">：</font>

```plain
npm i file-loader -D
```

```plain
import avatar from './avatar.png' // 导入打包后资源的路径
const img = new Image();
img.src = avatar;
document.body.append(img);
```

<font style="color:rgb(53, 53, 53);">配置规则</font>

```plain
module: {
  rules: [
    /******/
    {
      test: /\.png$/,
      use: 'file-loader',
    }
  ],
},
```

<font style="color:rgb(53, 53, 53);">打包后，在dist目录下生成了871132b331c17257fcba75273b57f9fe.png，这是将文件的hash值作为了打包后的文件名，当然，这也是可以自定义的。</font>

```plain
{
  test: /\.png$/,
  use: {
    loader: 'file-loader',
    options: {
      // 默认[hash].[ext]
      name: '[path][name].[ext]',
    }
  },
}
```

<font style="color:rgb(53, 53, 53);">这样就能保留图片的原始相对路径和名称。</font>

<h3 id="vK2Dh">url-loader</h3>

<font style="color:rgb(53, 53, 53);">file-loader拷贝文件到输出目录，而</font>[<font style="color:rgb(53, 53, 53);">url-loader</font>](https://v4.webpack.docschina.org/loaders/url-loader/)<font style="color:rgb(53, 53, 53);">通过</font>**<font style="color:rgb(53, 53, 53);">durl</font>**<font style="color:rgb(53, 53, 53);">的形式表示文件</font>

**shell**

```plain
npm i url-loader -D
```

<font style="color:rgb(53, 53, 53);">durl即Data URLs，可以通过url直接去表示文件的内容，不会产生任何请求</font>

```plain
// 一个html类型的文件内容，编码是utf-8
data:text/html;charset=UTF-8,<h1>html content</h1>
// 如果是图片这种无法直接通过文本表示的文件，则可以将文件内容进行base64编码
data:image/png;base64,iDAHAidhbaIADHA...AHiDAd
```

**<font style="color:rgb(53, 53, 53);">最佳实践：</font>**<font style="color:rgb(53, 53, 53);">配置小文件使用url-loader，大文件则使用file-loader</font>

```plain
{
  test: /\.(png|ico)$/,
  use: {
    loader: "url-loader",
    options: {
      name: "[path][name]_[hash:6].[ext]",
      limit: 50 * 1024, //小于50kb的进行编码
      // 超过这个大小，url-loader会自动调用file-loader
    },
  },
}
```

```plain
import { createImage } from "./module.js";
import avatar from './avatar.png'
import icon from './icon.ico'
document.body.append(createImage(avatar));
document.body.append(createImage(icon));
```

<h3 id="mggbT">Asset Modules</h3>

<font style="color:rgb(53, 53, 53);">webpack5使用</font>[<font style="color:#117CEE;">资源模块Asset Modules</font>](https://webpack.docschina.org/guides/asset-modules/)<font style="color:rgb(53, 53, 53);">来加载图片、字体等资源。</font>

<font style="color:rgb(53, 53, 53);">在webpack5之前，通常使用：raw-loader将文件导入为字符串，url-loader将文件作为durl内联到bundle中，file-loader将文件发送到输出目录</font>

<font style="color:rgb(53, 53, 53);">资源模块类型(asset module type)，通过添加 4 种新的模块类型，来替换所有这些 loader：</font>

1. `<font style="color:rgb(233, 105, 0);">asset/resource</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">发送一个单独的文件并导出 URL。之前通过使用 file-loader 实现。</font>
2. `<font style="color:rgb(233, 105, 0);">asset/inline</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">导出一个资源的 data URI。之前通过使用 url-loader 实现。</font>
3. `<font style="color:rgb(233, 105, 0);">asset/source</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">导出资源的源代码。之前通过使用 raw-loader 实现。</font>
4. `<font style="color:rgb(233, 105, 0);">asset</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">在导出一个 data URI 和发送一个单独的文件之间自动选择。之前通过使用 url-loader，并且配置资源体积限制实现。</font>

**<font style="color:rgb(53, 53, 53);">案例：</font>**

```plain
{
  test: /\.(png|jpg|svg|gif|ico)$/,
  // type选择类型
  type: "asset/resource",
  // 通过generator属性进行配置
  generator: {
    filename: "img/[name]_[hash:6][ext]",
  },
},
```

**js**



```plain
asset/inline{
  test: /\.(png|jpg|svg|gif|ico)$/,
  type: "asset/inline",
},
```

<font style="color:rgb(53, 53, 53);">最佳实践：type设为asset，添加一个parser属性，并且制定dataUrl的条件，添加maxSize属性；</font>

```plain
{
  test: /\.(png|jpg|svg|gif|ico)$/,
  type: "asset",
  generator: {
    filename: "img/[name]_[hash:6][ext]",
  },
  parser: {
    dataUrlCondition: {
      maxSize: 50 * 1024,//小于50kb进行编码，转为base64
    },
  },
},
```

<h2 id="jcGSI">babel-loader</h2>

<font style="color:rgb(53, 53, 53);">webpack由于打包需要，会去处理import和export，但对于其它ES6新特性，则不会去做兼容处理</font>

<font style="color:rgb(53, 53, 53);">如果需要将代码中的ES6进行转换，则需要</font>[<font style="color:rgb(53, 53, 53);">babel-loader</font>](https://webpack.docschina.org/loaders/babel-loader/)

```plain
// 安装babel-loader及其依赖的核心库和特性转换集合
npm install -D babel-loader @babel/core @babel/preset-env
```

**<font style="color:rgb(53, 53, 53);">注意：</font>**<font style="color:rgb(53, 53, 53);">babel只是转换JS代码的一个平台，还需要用其它的插件，如@babel/preset-env，通过该平台来转换ES6特性</font>

<font style="color:rgb(53, 53, 53);">进行配置：</font>

```plain
module: {
  rules: [
    {
      test: /\.js$/i,
      include: [
        path.resolve(__dirname, 'src')
      ],
      exclude: [
        path.resolve(__dirname, 'node_modules')
      ],
      loader: 'babel-loader',
      options: {
        presets: ["@babel/preset-env"]
      }
    },
  ]
}
```

<font style="color:rgb(53, 53, 53);">开启ESM转CommonJS(会导致Tree Shaking失效，不推荐开启)</font>

```plain
presets: [
  ["@babel/preset-env", {
    modules: "commonjs", // 开启ESM转CommonJS，默认："auto"
  }]
]
```

<font style="color:rgb(53, 53, 53);">这样就完成了简单的ES6转换，更完善的使用core-js@3兼容，后面再说吧。</font>

<h2 id="Pmsfh">资源加载方式</h2>

<font style="color:rgb(53, 53, 53);">除了在js文件中使用import加载资源，webpack还会自动处理其它加载资源的方式，如css文件中的url()、@import</font>

<font style="color:rgb(53, 53, 53);">例如：当css-loader在处理css文件时遇到url()时，会找到符合的规则对所需的资源进行处理，如使用asset/resource对图片资源处理</font>

```plain
/* main.css */
body{
  background-image: url(avatar.png);
  background-size: auto;
}

/* index.css */
@import './main.css';
body{
  background-color: #ccc;
}
```

<h2 id="zM3TD">开发loader</h2>

<font style="color:rgb(53, 53, 53);">尝试开发一个markdown-loader，深入了解loader的工作过程</font>

**<font style="color:rgb(53, 53, 53);">文档：</font>**[<font style="color:rgb(53, 53, 53);">编写loader</font>](https://www.webpackjs.com/contribute/writing-a-loader/)

**<font style="color:rgb(53, 53, 53);">功能：</font>**<font style="color:rgb(53, 53, 53);">将模块中所需的markdown资源转为html内容导入</font>

<font style="color:rgb(53, 53, 53);">在根目录新建</font>`<font style="color:rgb(233, 105, 0);">markdown-loader.js</font>`<font style="color:rgb(53, 53, 53);">，一个最简单的loader是一个函数，接收传入的资源内容，若该loader是最后一个执行的，返回结果必须是JS代码</font>

```plain
module.exports = source => {
  console.log(source)
  return 'console.log(source)'
}
```

<font style="color:rgb(53, 53, 53);">使用该loader</font>

```plain
{
  test: /\.md$/i,
  use: path.resolve(__dirname, 'markdown-loader.js'),
}
```

<font style="color:rgb(53, 53, 53);">在模块中导入markdown，webpack只会处理模块所依赖的资源</font>

```plain
import md from './01.md'
console.log(md)
```

<font style="color:rgb(53, 53, 53);">打包时控制台输出了markdown的内容。查看打包结果，loader返回的js也在其中，被一个IIFE包裹。</font>

<font style="color:rgb(53, 53, 53);">下面继续完成功能：</font>

<font style="color:rgb(53, 53, 53);">安装解析markdown内容的模块，使用</font>[<font style="color:rgb(53, 53, 53);">marked</font>](https://www.npmjs.com/package/marked)

```plain
npm i marked -D
```

<font style="color:rgb(53, 53, 53);">修改 </font>`<font style="color:rgb(233, 105, 0);">markdown-loader.js</font>`

```plain
const marked = require('marked');

module.exports = source => {
  console.log(source)
  const html = marked.parse(source)
  console.log(html)
  return 'console.log(source)'
}
```

<font style="color:rgb(53, 53, 53);">输出如下，现在loader已经能解析markdown文件了</font>

```plain
# 简介
这是一个**markdown**
<h1>简介</h1>
<p>这是一个<strong>markdown</strong></p>
```

<font style="color:rgb(53, 53, 53);">完善loader，将html暴露给模块使用，会作为模块中import markdown文件的default值</font>

```plain
const marked = require('marked');

module.exports = source => {
  const html = marked.parse(source)
  // html中存在一些字符，使用JSON.stringify进行转译
  return `export default ${JSON.stringify(html)}`
}
```

<font style="color:rgb(53, 53, 53);">现在，markdown-loader就完成了，模块导入的就是解析好的html内容</font>

```plain
import md from './01.md'
console.log(md)
// <h1>简介</h1>
// <p>这是一个<strong>markdown</strong></p>
```

<font style="color:rgb(53, 53, 53);">当然，markdown-loader也可以直接返回解析好的html内容，再交给loader管道中下一个loader进行处理，webpack只要求最后一个loader返回的需要是JS代码</font>

<font style="color:rgb(53, 53, 53);">处理html就需要安装html-loader，</font>`<font style="color:rgb(233, 105, 0);">npm i html-loader -D</font>`

<font style="color:rgb(53, 53, 53);">修改代码：</font>

```plain
{
  test: /\.md$/i,
  use: [
    'html-loader',
    path.resolve(__dirname, 'markdown-loader.js'),
  ]
}
```

```plain
const marked = require('marked');

module.exports = source => {
  const html = marked.parse(source)
  return html
}
```

<font style="color:rgb(53, 53, 53);">实现的功能也是一样的</font>

<h1 id="BCeWv">plugin</h1>

<font style="color:rgb(53, 53, 53);">loader用于处理资源的加载，而插件</font>[<font style="color:rgb(53, 53, 53);">plugin</font>](https://webpack.docschina.org/concepts/plugins/)<font style="color:rgb(53, 53, 53);">用于实现各种</font>**<font style="color:rgb(53, 53, 53);">自动化</font>**<font style="color:rgb(53, 53, 53);">操作，如压缩代码、替换内容、处理资源</font>

<font style="color:rgb(53, 53, 53);">官方</font>[<font style="color:rgb(53, 53, 53);">plugins</font>](https://webpack.docschina.org/plugins/)

<h2 id="RQuMG">打包分析插件</h2>

[<font style="color:rgb(53, 53, 53);">webpack-bundle-analyzer</font>](https://www.npmjs.com/package/webpack-bundle-analyzer)<font style="color:rgb(53, 53, 53);">是一个打包分析插件，使用交互式可缩放树形地图可视化，并输出文件的大小。可以方便开发人员检查打包后的文件拆分、分析文件大小。</font>

<font style="color:rgb(53, 53, 53);">每次打包时，会自动打开浏览器，访问</font>`<font style="color:rgb(233, 105, 0);">127.0.0.1:8888</font>`<font style="color:rgb(53, 53, 53);">查看项目结构</font>

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i webpack-bundle-analyzer -D</font>`

<font style="color:rgb(53, 53, 53);">webpack中，插件都需要导入后使用，且通常插件导出的都是一个class，需要new实例。配置项plugins是一个数组，保存插件的实例。</font>

```plain
const { BundleAnalyzerPlugin } = require('webpack-bundle-analyzer');
/*****/
plugins: [
  new BundleAnalyzerPlugin(),
],
```

<h2 id="RKMW1">自动生成HTML</h2>

<font style="color:rgb(53, 53, 53);">手动在根目录创建index.html，并配置打包好的JS等资源的路径，这样硬编码过于麻烦且易出错</font>

<font style="color:rgb(53, 53, 53);">可以使用</font>[<font style="color:rgb(53, 53, 53);">html-webpack-plugin</font>](https://webpack.docschina.org/plugins/html-webpack-plugin/)<font style="color:rgb(53, 53, 53);">简化HTML文件的创建，自动引入打包好的JS模块，这对于那些文件名中包含哈希值，并且哈希值会随着每次编译而改变的 webpack 包特别有用。</font>

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i html-webpack-plugin --D</font>`

```plain
const HtmlWebpackPlugin = require('html-webpack-plugin')
plugins: [
  new HtmlWebpackPlugin({
    template: path.resolve(__dirname, './index.html'), // 自定义模板
    inject: 'body', // 插入到body
    filename: 'index.html', // 输出文件名，默认index.html
    title: 'webpack测试', // 自定义title，通过<%= htmlWebpackPlugin.options.title %>在html中使用
    minify: true, // 压缩
  }),
]
```

<font style="color:rgb(53, 53, 53);">修改根目录下的index.html，使其作为一个模板</font>

```plain
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title><%= htmlWebpackPlugin.options.title %></title>
</head>
<body>
  <!-- 去掉js文件的引入，插件会自动引入 -->
  <!-- <script src="dist/main.js"></script> -->
</body>
</html>
```

<font style="color:rgb(53, 53, 53);">查看打包后的index.html</font>

```plain
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>webpack测试</title>
</head>
<body>
  <script defer src="main_0cc0be.js"></script>
</body>
</html>
```

<font style="color:rgb(53, 53, 53);">html-webpack-plugin还有其它的配置项，查看官方仓库文档：</font>[<font style="color:rgb(53, 53, 53);">配置项</font>](https://github.com/jantimon/html-webpack-plugin#options)

<font style="color:rgb(53, 53, 53);">若是多页面、多个html文件，则创建多个插件实例加入到plugins数组中</font>

<h2 id="JC5om">拷贝文件</h2>

<font style="color:rgb(53, 53, 53);">通常项目中还有一些无需打包的静态文件存放于public目录，这些资源同样需要输出到dist</font>

[<font style="color:rgb(53, 53, 53);">copy-webpack-plugin</font>](https://webpack.docschina.org/plugins/copy-webpack-plugin/)

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i copy-webpack-plugin -D</font>`

**js**

```plain
const CopyPlugin = require("copy-webpack-plugin");
plugins: [
  new CopyPlugin({
    patterns: [
      // 复制public文件夹内的文件到{output}中
      { from: path.resolve(__dirname, 'public'), to: "" },
    ],
  }),
]
```

<h2 id="KjyCM">开发plugin</h2>

<font style="color:rgb(53, 53, 53);">相较于loader只作用于模块加载，plugin的作用范围更广。plugin通过常见的</font>**<font style="color:rgb(53, 53, 53);">钩子机制</font>**<font style="color:rgb(53, 53, 53);">实现，就像Vue生命周期提供的钩子一样。</font>

<font style="color:rgb(53, 53, 53);">webpack提供了很多打包过程中的</font>**<font style="color:rgb(53, 53, 53);">钩子</font>**<font style="color:rgb(53, 53, 53);">，plugin向这些钩子上</font>**<font style="color:rgb(53, 53, 53);">挂载</font>**<font style="color:rgb(53, 53, 53);">任务，并获取</font>**<font style="color:rgb(53, 53, 53);">上下文</font>**<font style="color:rgb(53, 53, 53);">，来实现对资源的操作等功能。</font>

<font style="color:rgb(53, 53, 53);">钩子相关文档：</font>[<font style="color:rgb(53, 53, 53);">compiler-hooks</font>](https://webpack.docschina.org/api/compiler-hooks/)

<font style="color:rgb(53, 53, 53);">webpack要求plugin必须是一个函数，或一个</font>**<font style="color:rgb(53, 53, 53);">包含apply方法</font>**<font style="color:rgb(53, 53, 53);">的对象，通常是定义一个包含apply方法的类</font>

<font style="color:rgb(53, 53, 53);">新建</font>`<font style="color:rgb(233, 105, 0);">myPlugin.js</font>`

**js**



<font style="color:rgb(53, 53, 53);">现在开发一个用于清除webpack生成的</font>`<font style="color:rgb(233, 105, 0);">/******/</font>`<font style="color:rgb(53, 53, 53);">注释，以方便阅读打包后的JS代码</font>

<font style="color:rgb(53, 53, 53);">明确了功能，考虑需要用到哪些钩子，显然，清除注释要在输出文件前执行，对要输出的内容进行处理。</font>[<font style="color:rgb(53, 53, 53);">emit</font>](https://webpack.docschina.org/api/compiler-hooks/#emit)<font style="color:rgb(53, 53, 53);">钩子符合需求，这个钩子在输出 asset 到 output 目录之前执行。</font>

**js**

```plain
export default class {
  // apply接收一个compiler对象参数
  // 这个对象包含了打包过程中所有信息以及用于注册钩子函数
  apply(compiler) {}
}
```

```plain
export default class {
  // apply接收一个compiler对象参数
  // 这个对象包含了打包过程中所有信息以及用于注册钩子函数
  apply(compiler) {
    // 通过hooks属性访问钩子，tap方法注册钩子函数
    // tap方法第一个参数为plugin名，第二个参数是接收了compilation对象的钩子函数
    compiler.hooks.emit.tap('MyPlugin', compilation => {
      // compilation是此次打包过程中的上下文，存放了打包过程的信息和结果
      // compilation.assets获取即将输出的资源文件信息
      for (const name in compilation.assets) {
        console.log(name); // 输出文件名
      }
    })
  }
}
```

<font style="color:rgb(53, 53, 53);">使用插件</font>

**js**

```plain
const MyPlugin = require('./myPlugin.js');
plugins: [
  new MyPlugin(),
]
```

<font style="color:rgb(53, 53, 53);">输出：</font>

**shell**

```plain
main_28990539038fea465479.js
img/avatar_871132b331c17257fcba.png
img/icon_36fa45932bf38a34e9af.ico
favicon.ico
index.html
```

<font style="color:rgb(53, 53, 53);">插件已经能读取到打包后的文件名，接下来通过正则替换来处理JS文件</font>

**js**

```javascript
module.exports = class {
  #isJSFile(filename) {
    // 使用正则表达式检查文件名是否以 .js 结尾
    return /\.js$/i.test(filename);
  }

  // apply接收一个compiler对象参数
  // 这个对象包含了打包过程中所有信息以及用于注册钩子函数
  apply(compiler) {
    // 通过hooks属性访问钩子，tap方法注册钩子函数
    // tap方法第一个参数为plugin名，第二个参数是接收了compilation对象的钩子函数
    compiler.hooks.emit.tap('MyPlugin', compilation => {
      // compilation是此次打包过程中的上下文，存放了打包过程的信息和结果
      // compilation.assets获取即将输出的资源文件信息
      for (const name in compilation.assets) {
        // console.log(name);
        // 使用source方法获取文件内容
        if(this.#isJSFile(name)){
          let content = compilation.assets[name].source();
          // 使用正则去除webpack生成的/******/
          content = content.replace(/\/\*{3,}\//g, '');
          // 覆盖文件信息
          compilation.assets[name] = {
            // 覆盖内容
            source: () => content,
            // webpack要求指定大小
            size: () => content.length
          }
        }
      }
    })
  }
}
```

<font style="color:rgb(53, 53, 53);">现在，打包的JS文件内容已经去除了</font>`<font style="color:rgb(233, 105, 0);">/******/</font>`

<font style="color:rgb(53, 53, 53);">但控制台有警告信息：</font>

**shell**

```plain
(node:76292) [DEP_WEBPACK_COMPILATION_ASSETS] DeprecationWarning: Compilation.assets will be frozen in future, all modifications are deprecated.
BREAKING CHANGE: No more changes should happen to Compilation.assets after sealing the Compilation.
        Do changes to assets earlier, e. g. in Compilation.hooks.processAssets.
        Make sure to select an appropriate stage from Compilation.PROCESS_ASSETS_STAGE_*.
(Use `node --trace-deprecation ...` to show where the warning was created)
```

<font style="color:rgb(53, 53, 53);">这是因为Webpack5将在未来版本冻结</font>`<font style="color:rgb(233, 105, 0);">compilation.assets</font>`<font style="color:rgb(53, 53, 53);">，需在</font>`<font style="color:rgb(233, 105, 0);">compiler.hooks.thisCompilation</font>`<font style="color:rgb(53, 53, 53);">钩子中使用 Compilation 中的 processAssets hook 来对资源进行再处理</font>

**js**

```plain
module.exports = class {
  #isJSFile(filename) {
    // 使用正则表达式检查文件名是否以 .js 结尾
    return /\.js$/i.test(filename);
  }

  // apply接收一个compiler对象参数
  // 这个对象包含了打包过程中所有信息以及用于注册钩子函数
  apply(compiler) {
    // 使用thisCompilation钩子，在 compilation 对象创建时执行一些自定义逻辑
    compiler.hooks.thisCompilation.tap('MyPlugin', compilation => {
      // processAssets钩子用于在 webpack 编译完成后，但在最终资源输出之前，处理资源文件的阶段执行插件代码
      compilation.hooks.processAssets.tap(
        {
          name: 'MyPlugin',
          // https://webpack.docschina.org/api/compilation-hooks/#list-of-asset-processing-stages
          stage: compilation.PROCESS_ASSETS_STAGE_OPTIMIZE, // 以通用的方式优化已有asset
        },
        (assets) => {
          for (const name in assets) {
            if (this.#isJSFile(name)) {
              // 使用正则表达式去除块注释
              const content = assets[name].source().replace(/\/\*{3,}\//g, '');
              // 覆盖文件信息
              assets[name] = {
                source: () => content,
                size: () => content.length,
              };
            }
          }
        }
      );
    })
  }
}
```

<h1 id="hyJBV">优化开发过程</h1>

<font style="color:rgb(53, 53, 53);">项目打包过程已经自动化了，但开发过程仍然在手动操作</font>

<font style="color:rgb(53, 53, 53);">编写代码->命令打包->运行应用->刷新浏览器，这个繁琐的过程也需要自动化，以提高开发效率</font>

<font style="color:rgb(53, 53, 53);">提出下面的需求：</font>

1. <font style="color:rgb(53, 53, 53);">以 HTTP Server 运行，而不是打开文件浏览</font>
2. <font style="color:rgb(53, 53, 53);">自动编译 + 自动刷新</font>
3. <font style="color:rgb(53, 53, 53);">提供 Source Map 支持，方便调试</font>

<h2 id="SwxYz">watch工作模式</h2>

<font style="color:rgb(53, 53, 53);">处于watch工作模式时，webpack会监听文件变化，自动重新打包</font>

<font style="color:rgb(53, 53, 53);">添加watch配置：</font>

**js**

```plain
module.exports = {
  watch: true,
}
```

<h2 id="MMMYw">DevServer</h2>

[<font style="color:rgb(53, 53, 53);">webpack dev server</font>](https://webpack.docschina.org/configuration/dev-server)<font style="color:rgb(53, 53, 53);">提供了HTTP Server，集成了自动编译和自动刷新浏览器的功能。</font>

<font style="color:rgb(53, 53, 53);">该插件会将将打包结果暂时存放于内存，而不输出于硬盘，以提高性能。</font>

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i webpack-dev-server -D</font>`

**js**

添加配置

```plain
module.exports = {
  // 配置开发服务器
  devServer: {
    // 服务器主机
    host: 'localhost',
    // 服务器端口
    port: 8080,
    // 启用Gzip
    compress: true,
    // CopyPlugin通常只在项目上线时去使用，开发时通常将静态资源目录配置给devServer，以提高性能
     // 使用static配置从目录提供静态文件的选项，默认public
    static: {
      // 告诉服务器从哪里提供内容
      directory: path.join(__dirname, 'public'),
    },
  }
}
```

<font style="color:rgb(53, 53, 53);">添加命令脚本</font>

**json**

```plain
{
  "scripts": {
    "serve": "webpack serve"
  }
}
```

<font style="color:rgb(53, 53, 53);">使用命令运行</font>`<font style="color:rgb(233, 105, 0);">npm run serve</font>`

<h2 id="d1fjn">代理API服务</h2>

<font style="color:rgb(53, 53, 53);">前后端同源部署时，本地开发在请求api时可能有cors问题，可以使用开发服务器代理api请求，服务器间通信就不存在cors了</font>

<font style="color:rgb(53, 53, 53);">DevServer就支持</font>`<font style="color:rgb(233, 105, 0);">proxy</font>`<font style="color:rgb(53, 53, 53);">配置api代理，</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/configuration/dev-server/#devserverproxy)

**js**

```plain
devServer: {
  proxy: {
    // 代理api路径
    '/api': {
      // localhost:8080/api/user -> api.github.com/api/user
      target: 'https://api.github.com',
      // 请求路径重写 /api/user -> /user
      pathRewrite: { '^/api': '' },
      // 将 host 请求头修改为 target 的 URL
      changeOrigin: true,
    },
  },
}
```

<h2 id="nI3ag">Source Map</h2>

<font style="color:rgb(53, 53, 53);">前端工程化后，源代码和运行代码几乎完全不同，调试和报错都是基于运行代码，调试源代码就成了问题</font>

<font style="color:rgb(53, 53, 53);">Source Map用于映射源代码和运行代码之间的关系</font>

<font style="color:rgb(53, 53, 53);">一个Source Map的组成：</font>

**json**

```plain
{
  "version": 3, // 当前Map使用的Source Map标准版本
  "sources": ["main.js"], // 记录源文件的名称，可以是多个文件
  "names": ["global",/****/], // 源代码使用的成员名称，如变量的原名
  "mappings": ";/****/" // 核心，记录源码和运行代码一些字符的映射关系
}
```

<font style="color:rgb(53, 53, 53);">通过一行特定格式的注释引入Source Map</font>

**js**

```plain
//# sourceMappingURL=main.map
```

<font style="color:rgb(53, 53, 53);">如果Source Map不起作用，需在浏览器控制台-设置-偏好设置中启用JavaScript源代映射</font>

<font style="color:rgb(53, 53, 53);">使用</font>[<font style="color:rgb(53, 53, 53);">Devtool</font>](https://webpack.docschina.org/configuration/devtool/)<font style="color:rgb(53, 53, 53);">在webpack中配置Source Map：</font>

**js**

```plain
module.exports = {
  devtool: 'source-map', // 值为Source Map工作模式
}
```

<font style="color:rgb(53, 53, 53);">相关文章：</font>[<font style="color:rgb(53, 53, 53);">一文搞懂SourceMap以及webpack devtool</font>](https://juejin.cn/post/6960941899616092167)

<font style="color:rgb(53, 53, 53);">Source Map工作模式：</font>

**text**

```plain
[inline-|hidden-|eval-][nosources-][cheap-[module-]]source-map
```

1. `<font style="color:rgb(233, 105, 0);">inline-</font>`<font style="color:rgb(53, 53, 53);"> 将SourceMap内联到原始文件中，而不是创建一个单独的文件。</font>
2. `<font style="color:rgb(233, 105, 0);">hidden-</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">仍然会生成.map文件，但是打包后的代码中没有sourceMappingURL，即浏览器不会加载.map文件，控制台中看不到源代码。Map生成后只供服务端分析使用，前端将出错的行列传给服务端。</font>
3. `<font style="color:rgb(233, 105, 0);">eval-</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">通过eval包裹每个模块打包后代码以及对应生成的SourceMap（不实际生成），因为eval中为字符串形式，进行字符串处理会提升rebuild的速度。</font>
4. `<font style="color:rgb(233, 105, 0);">nosources-</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">不包含 sourcesContent 内容，调试时只能看到文件信息和行信息，无法看到源码。</font>
5. `<font style="color:rgb(233, 105, 0);">cheap-[module-]</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">只定位到源码所在的行，不定位至具体的列，构建速度有所提升。如果只用 cheap ，显示的是 loader 编译之后的源代码，加上 module 后会显示编译之前的源代码。</font>

<font style="color:rgb(53, 53, 53);">如何选择devtool：</font>

1. **<font style="color:rgb(53, 53, 53);">production：</font>**<font style="color:rgb(53, 53, 53);">none，source-map，hidden-source-map，nosources-source-map</font>
2. **<font style="color:rgb(53, 53, 53);">development：</font>**<font style="color:rgb(53, 53, 53);">eval，eval-source-map，eval-cheap-source-map，eval-cheap-module-source-map</font>

<font style="color:rgb(53, 53, 53);">开发环境下，需要频繁的修改代码，更多地考虑的开发效率和调试效率，所以更多关注 performance 中 rebuild 的性能。生产环境下，不必过多关注打包性能，主要考虑 quality 代码的保护性、出错的定位速度已经安全性</font>

<h2 id="Zfh6G">热替换HMR</h2>

<font style="color:rgb(53, 53, 53);">监视模块变动后重新打包、自动刷新会导致页面的一些状态丢失（输入的文本内容），如果能让页面不刷新，模块也能更新，这样的开发体验会好很多</font>

<font style="color:rgb(53, 53, 53);">模块热替换</font>[<font style="color:rgb(53, 53, 53);">HMR</font>](https://webpack.docschina.org/configuration/dev-server/#devserverhot)<font style="color:rgb(53, 53, 53);">(Hot Module Replacement)可以实现无刷更新模块，</font>[<font style="color:rgb(53, 53, 53);">「webpack 核心特性」模块热替换(HMR)</font>](https://juejin.cn/post/6870258201384714253)

<font style="color:rgb(53, 53, 53);">HMR作用：</font>

1. <font style="color:rgb(53, 53, 53);">保留在完全重新加载页面期间丢失的应用程序状态。</font>
2. <font style="color:rgb(53, 53, 53);">只更新变更内容，以节省宝贵的开发时间。</font>
3. <font style="color:rgb(53, 53, 53);">在源代码中 CSS/JS 产生修改时，会立刻在浏览器中进行更新，这几乎相当于在浏览器 devtools 直接更改样式。</font>

**js**

使用HMR

```plain
devServer: {
  hot: true, // 开启HMR
  // 在构建失败时不刷新页面作为回退
  // hot: 'only',
}
```

<font style="color:rgb(53, 53, 53);">从webpack-dev-server v4开始，HMR已默认启用。会自动应用HotModuleReplacementPlugin插件</font>

**<font style="color:rgb(53, 53, 53);">注意：</font>**<font style="color:rgb(53, 53, 53);">HMR并不是开箱即用，还需要使用</font>[<font style="color:rgb(53, 53, 53);">HMR-API</font>](https://webpack.docschina.org/api/hot-module-replacement/)<font style="color:rgb(53, 53, 53);">手动处理模块的热替换逻辑，否则还会自动刷新，部分loader和插件如style-loader已经处理好了css的热更新逻辑，在Vue等框架下开发，框架本身也处理好了HMR</font>

<font style="color:rgb(53, 53, 53);">使用</font>[<font style="color:rgb(53, 53, 53);">HMR-API</font>](https://webpack.docschina.org/api/hot-module-replacement/)<font style="color:rgb(53, 53, 53);">手动处理JS模块热替换：</font>

**js**

通常在入口模块统一做处理

```plain
if (module.hot) {
  module.hot.accept('./library.js', function() {
    // 对更新过的 library 模块做些事情...
  });
}
// or
if (import.meta.webpackHot) {
  import.meta.webpackHot.accept('./library.js', function () {
    // Do something with the updated library module…
  });
}

// accept方法
module.hot.accept(
  dependencies, // 可以是一个字符串或字符串数组
  callback // 用于在模块更新后触发的函数
  errorHandler // (err, {moduleId, dependencyId}) => {}
);
```

<font style="color:rgb(53, 53, 53);">案例：</font>

**js**

src/index.js

```plain
import { appendMarkdown } from "./module.js";
import md from './01.md'
let mde = appendMarkdown(md);

if (module.hot) {
  // 处理01.md的更新
  module.hot.accept('./01.md', () => {
    // 热重载，先移除原来的
    document.body.removeChild(mde);
    // 再创建新的
    mde = appendMarkdown(md);
  });
}
```

<font style="color:rgb(53, 53, 53);">热重载的需要根据自己的业务逻辑去实现，没有通用的方法，这也是webpack没有提供JS模块HMR的原因。</font>

<font style="color:rgb(53, 53, 53);">打包后，HMR相关代码会被自动去除</font>

<h1 id="HfM4W">不同环境的配置</h1>

<font style="color:rgb(53, 53, 53);">不同的环境需要不同的webpack配置，主要是区分生产和开发环境，</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/configuration/)

<font style="color:rgb(53, 53, 53);">区分环境有两种方式</font>

1. <font style="color:rgb(53, 53, 53);">配置函数中判断env，返回不同的配置信息</font>
2. <font style="color:rgb(53, 53, 53);">创建多个配置文件对应不同的环境（推荐）</font>

<h2 id="c4N7I">判断env</h2>

<font style="color:rgb(53, 53, 53);">webpack配置导出一个函数而非对象，</font>[<font style="color:rgb(53, 53, 53);">导出函数</font>](https://webpack.docschina.org/configuration/configuration-types/#exporting-a-function)<font style="color:rgb(53, 53, 53);">，</font>[<font style="color:rgb(53, 53, 53);">环境变量</font>](https://webpack.docschina.org/guides/environment-variables/)

**js**

```plain
/**
 * 
 * @param {string} env 环境名参数
 * @param {array} argv cli传递的所有参数
 * @returns {object} webpack配置
 */
module.exports = (env, argv) => {
  console.log(env);
  // 默认的通用配置
  const config = {
    mode: 'none',
    // 生成源映射以方便调试
    devtool: 'eval-source-map',
    // watch: true,
    context: path.resolve(__dirname, 'src'),
    entry: {
      main: ['./index.js', './main.js'],
    },
    output: {
      path: path.resolve(__dirname, 'dist'),
      filename: '[name]_[contenthash].js',
      clean: true,
    },
    module: {
      rules: [
        {
          // 正则匹配loader要处理的资源
          test: /\.css$/i,
          // 逆序执行，从右往左
          use: ['style-loader', 'css-loader'],
        },
        {
          test: /\.(png|jpg|svg|gif|ico)$/,
          type: "asset",
          generator: {
            filename: "img/[name]_[contenthash][ext]",
          },
          parser: {
            dataUrlCondition: {
              maxSize: 50 * 1024,//小于50kb进行编码，转为base64
            },
          },
        },
        {
          test: /\.js$/i,
          include: [
            path.resolve(__dirname, 'src')
          ],
          exclude: [
            path.resolve(__dirname, 'node_modules')
          ],
          loader: 'babel-loader',
          options: {
            presets: ["@babel/preset-env"]
          }
        },
        {
          test: /\.md$/i,
          use: path.resolve(__dirname, 'markdown-loader.js'),
        }
      ],
    },
    plugins: [
      new HtmlWebpackPlugin({
        template: path.resolve(__dirname, './index.html'), // 自定义模板
        inject: 'body', // 插入到body
        filename: 'index.html', // 输出文件名，默认index.html
        title: 'webpack测试', // 自定义title，通过<%= htmlWebpackPlugin.options.title %>在html中使用
        minify: true, // 压缩
      }),
    ],
    // 配置开发服务器
    devServer: {
      // 服务器主机
      host: 'localhost',
      // 服务器端口
      port: 8080,
      // 使用HMR
      hot: true,
      // 启用Gzip
      compress: true,
      // CopyPlugin通常只在项目上线时去使用，开发时通常将静态资源目录配置给devServer，以提高性能
      // 使用static配置从目录提供静态文件的选项，默认public
      static: {
        // 告诉服务器从哪里提供内容
        directory: path.join(__dirname, 'public'),
      },
      proxy: {
        // 代理api路径
        '/api': {
          // localhost:8080/api/user -> api.github.com/api/user
          target: 'https://api.github.com',
          // 请求路径重写 /api/user -> /user
          pathRewrite: { '^/api': '' },
          // 将 host 请求头修改为 target 的 URL
          changeOrigin: true,
        },
      },
    }
  }
  // 判断环境，修改配置
  if (env.production) { // 生产环境
    config.mode = 'production';
    config.devtool = false;
    config.plugins = [
      ...config.plugins,
      new CopyPlugin({
        patterns: [
          // 复制public文件夹内的文件到{output}中
          { from: path.resolve(__dirname, 'public'), to: "" },
        ],
      }),
    ];
  } else if (env.development) { // 开发环境
    config.mode = 'development';
  }

  return config
}
```

**shell**

```plain
npx webpack --env production
npx webpack --env development
```

<h2 id="M29q7">多配置文件</h2>

<font style="color:rgb(53, 53, 53);">若项目较大配置复杂，就不适合用判断env的方式，写多个配置文件更清晰明了，</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/guides/production/)

<font style="color:rgb(53, 53, 53);">通常有三个配置文件：</font>

1. `<font style="color:rgb(233, 105, 0);">webpack.common.js</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">通用配置文件，写一些项目的通用基础配置</font>
2. `<font style="color:rgb(233, 105, 0);">webpack.dev.js</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">开发配置文件</font>
3. `<font style="color:rgb(233, 105, 0);">webpack.prod.js</font>`<font style="color:rgb(53, 53, 53);"> </font><font style="color:rgb(53, 53, 53);">生产配置文件</font>

<font style="color:rgb(53, 53, 53);">安装</font>[<font style="color:rgb(53, 53, 53);">webpack-merge</font>](https://www.npmjs.com/package/webpack-merge)<font style="color:rgb(53, 53, 53);">合并配置对象：</font>`<font style="color:rgb(233, 105, 0);">npm i webpack-merge -D</font>`

**js**

webpack.common.js

```plain
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  mode: 'none',
  // 生成源映射以方便调试
  devtool: 'source-map',
  // watch: true,
  context: path.resolve(__dirname, 'src'),
  entry: {
    main: ['./index.js', './main.js'],
  },
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name]_[contenthash].js',
    clean: true,
  },
  //警告 webpack 的性能提示
  performance: {
    hints: 'warning',
    //入口起点的最大体积
    maxEntrypointSize: 1024 * 1024 * 10,
    //生成文件的最大体积
    maxAssetSize: 1024 * 1024,
    //只给出 js 文件的性能提示
    assetFilter: function (assetFilename) {
      return /\.js$/.test(assetFilename);
    }
  },
  module: {
    rules: [
      {
        // 正则匹配loader要处理的资源
        test: /\.css$/i,
        // 逆序执行，从右往左
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.(png|jpg|svg|gif|ico)$/,
        type: "asset",
        generator: {
          filename: "img/[name]_[contenthash][ext]",
        },
        parser: {
          dataUrlCondition: {
            maxSize: 50 * 1024,//小于50kb进行编码，转为base64
          },
        },
      },
      {
        test: /\.js$/i,
        include: [
          path.resolve(__dirname, 'src')
        ],
        exclude: [
          path.resolve(__dirname, 'node_modules')
        ],
        loader: 'babel-loader',
        options: {
          presets: ["@babel/preset-env"]
        }
      },
      {
        test: /\.md$/i,
        use: path.resolve(__dirname, 'markdown-loader.js'),
      }
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, './index.html'), // 自定义模板
      inject: 'body', // 插入到body
      filename: 'index.html', // 输出文件名，默认index.html
      title: 'webpack测试', // 自定义title，通过<%= htmlWebpackPlugin.options.title %>在html中使用
      minify: true, // 压缩
    }),
  ],
  // 配置开发服务器
  devServer: {
    // 服务器主机
    host: 'localhost',
    // 服务器端口
    port: 8080,
    // 使用HMR
    hot: true,
    // 启用Gzip
    compress: true,
    // CopyPlugin通常只在项目上线时去使用，开发时通常将静态资源目录配置给devServer，以提高性能
    // 使用static配置从目录提供静态文件的选项，默认public
    static: {
      // 告诉服务器从哪里提供内容
      directory: path.join(__dirname, 'public'),
    },
    proxy: {
      // 代理api路径
      '/api': {
        // localhost:8080/api/user -> api.github.com/api/user
        target: 'https://api.github.com',
        // 请求路径重写 /api/user -> /user
        pathRewrite: { '^/api': '' },
        // 将 host 请求头修改为 target 的 URL
        changeOrigin: true,
      },
    },
  }
}
```

**js**

webpack.dev.js

```plain
const common = require("./webpack.common");
const { merge } = require("webpack-merge");

module.exports = merge(common, {
  mode: 'development',
  devtool: 'eval-source-map',
});
```

**js**

webpack.prod.js

```plain
const common = require("./webpack.common");
const path = require('path');
const CopyPlugin = require("copy-webpack-plugin");
const { merge } = require("webpack-merge");

module.exports = merge(common, {
  mode: 'production',
  devtool: false,
  plugins: [
    new CopyPlugin({
      patterns: [
        // 复制public文件夹内的文件到{output}中
        { from: path.resolve(__dirname, 'public'), to: "" },
      ],
    }),
  ],
});
```

<font style="color:rgb(53, 53, 53);">通过 —config 标志使用不同的配置文件</font>

**json**

```plain
"scripts": {
  "build": "webpack --config webpack.prod.js",
  "build-dev": "webpack --config webpack.dev.js",
  "prod": "webpack serve --config webpack.prod.js",
  "dev": "webpack serve --config webpack.dev.js"
},
```

<h1 id="Fhu5a">内置插件</h1>

<font style="color:rgb(53, 53, 53);">webpack本身内置了很多插件对bundle进行优化，且一些插件在</font>`<font style="color:rgb(233, 105, 0);">mode: production</font>`<font style="color:rgb(53, 53, 53);">时会自动开启，进行一些通用的优化操作，</font>[<font style="color:rgb(53, 53, 53);">优化(Optimization)</font>](https://webpack.docschina.org/configuration/optimization/)

<h2 id="iuMQm">DefinePlugin</h2>

[<font style="color:rgb(53, 53, 53);">DefinePlugin</font>](https://webpack.docschina.org/plugins/define-plugin/)<font style="color:rgb(53, 53, 53);">用来注入全局成员，在</font>**<font style="color:rgb(53, 53, 53);">编译时</font>**<font style="color:rgb(53, 53, 53);">将代码中的变量替换为其他值或表达式</font>

<font style="color:rgb(53, 53, 53);">在</font>`<font style="color:rgb(233, 105, 0);">mode: production</font>`<font style="color:rgb(53, 53, 53);">时，DefinePlugin默认启用，并注入了</font>`<font style="color:rgb(233, 105, 0);">process.env.NODE_ENV</font>`<font style="color:rgb(53, 53, 53);">，许多第三方的模块使用这个常量来判断当前环境</font>

<font style="color:rgb(53, 53, 53);">DefinePlugin接收一个对象，对象中的值若为字符串，将被作为代码片段使用，</font>

**js**

使用API_BASE_URL区分生产和开发环境API接口

```plain
const webpack = require('webpack');

plugins: [
  new webpack.DefinePlugin({
    // 使用JSON.stringify作为表示字符串的代码片段
    API_BASE_URL: JSON.stringify('http://api.github.com'),
  }),
],

console.log(API_BASE_URL)
```

<h2 id="zHa1p">Tree Shaking</h2>

[<font style="color:rgb(53, 53, 53);">Tree Shaking</font>](https://webpack.docschina.org/guides/tree-shaking/)<font style="color:rgb(53, 53, 53);">用于移除JS上下文中的</font>**<font style="color:rgb(53, 53, 53);">未引用</font>**<font style="color:rgb(53, 53, 53);">代码(dead-code)，</font>**<font style="color:rgb(53, 53, 53);">基于ESM</font>**

<font style="color:rgb(53, 53, 53);">在</font>`<font style="color:rgb(233, 105, 0);">mode: production</font>`<font style="color:rgb(53, 53, 53);">时Tree Shaking功能自动开启，也可通过配置开启</font>

**js**

```plain
module.exports = {
  optimization: {
    // 只导出使用了的成员
    usedExports: true,
  },
}
```

<font style="color:rgb(53, 53, 53);">测试代码：</font>

**js**

src/utils.js

```plain
const info = {
  name: 'chuckle',
  age: '20',
}
export function getName(){
  return info.name
}
export function getAge(){
  return info.age
}
export function logName(){
  console.log(info.name);
}
export function logAge(){
  console.log(info.age);
}
```

<font style="color:rgb(53, 53, 53);">打包结果，仍然存在未使用的代码片段，这是因为usedExports只是标记了未引用代码，而</font>`<font style="color:rgb(233, 105, 0);">optimization.minimize</font>`<font style="color:rgb(53, 53, 53);">才是用于压缩bundle，并去除未引用代码，两者搭配才实现了Tree Shaking</font>

**js**

```plain
/* harmony export */ __webpack_require__.d(__webpack_exports__, {
/* harmony export */   logName: () => (/* binding */ logName)
/* harmony export */ });
/* unused harmony exports getName, getAge, logAge */
var info = {
  name: 'chuckle',
  age: '20'
};
function getName() {
  return info.name;
}
function getAge() {
  return info.age;
}
function logName() {
  var _console;
  /* eslint-disable */(_console = console).log.apply(_console, _toConsumableArray(oo_oo("3634127370_12_2_12_24_4", info.name)));
}
function logAge() {
  var _console2;
  /* eslint-disable */(_console2 = console).log.apply(_console2, _toConsumableArray(oo_oo("3634127370_15_2_15_23_4", info.age)));
}
```

<h3 id="rFB9Q">压缩代码去除未引用</h3>

`<font style="color:rgb(233, 105, 0);">optimization.minimize</font>`<font style="color:rgb(53, 53, 53);">压缩bundle并去除未引用代码，</font>`<font style="color:rgb(233, 105, 0);">mode: production</font>`<font style="color:rgb(53, 53, 53);">默认开启</font>

**js**

```plain
module.exports = {
  //...
  optimization: {
    minimize: true,
  },
};
```

<font style="color:rgb(53, 53, 53);">打包后，未使用过的代码已经去除</font>

**js**

```plain
e.d(_,{logName:()=>d});var t={name:"chuckle",age:"20"};
```

<h3 id="Lnxqo">副作用</h3>

<font style="color:rgb(53, 53, 53);">将文件标记为</font>[<font style="color:rgb(53, 53, 53);">side-effect-free</font>](https://webpack.docschina.org/guides/tree-shaking/#mark-the-file-as-side-effect-free)<font style="color:rgb(53, 53, 53);">(无副作用)安全地删除未用到的export，目的是为了给Tree Shaking更大的优化空间</font>

<font style="color:rgb(53, 53, 53);">副作用：模块执行时，除了导出成员之外所作的事情</font>

[<font style="color:rgb(53, 53, 53);">optimization.sideEffects</font>](https://webpack.docschina.org/configuration/optimization/#optimizationsideeffects)<font style="color:rgb(53, 53, 53);">告知webpack去辨识package.json中的副作用标记或规则，以跳过那些当导出不被使用且被标记不包含副作用的模块。</font>

**js**

```plain
optimization: {
  sideEffects: true, // 开启
},
```

**json**

```plain
"sideEffects": false, // 项目所有模块都无副作用
// or
"sideEffects": ["*.css"], // 使用css-loader且在css文件中使用import时很有必要
```

<font style="color:rgb(53, 53, 53);">常见副作用代码：</font>

**js**

src/pad.js

```plain
// 数字前补全0
Number.prototype.pad = function (size) {
  let result = String(this);
  while (result.length < size) {
    result += '0';
  }
  return result;
}

// 导入使用
import './pad'
```

<font style="color:rgb(53, 53, 53);">若没有标记副作用，打包会排除该代码片段</font>

**text**

```plain
Uncaught TypeError: 8.pad is not a function
  at ./main.js (main.js:17:72)
  at __webpack_require__ (bootstrap:24:1)
  at startup:7:1
  at startup:7:1
```

<font style="color:rgb(53, 53, 53);">标记副作用</font>

**json**

```plain
"sideEffects": ["*.css", "./src/pad.js"],
```

<h2 id="R9T71">模块分包</h2>

<font style="color:rgb(53, 53, 53);">webpack会将所有小颗粒度的模块，从入口模块开始打包到一个JS模块，若项目较大，bundle也会很大，一些模块可以分包出来，减小bundle的体积，</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/guides/code-splitting/)

<font style="color:rgb(53, 53, 53);">模块分包办法：</font>

1. <font style="color:rgb(53, 53, 53);">多入口打包</font>
2. <font style="color:rgb(53, 53, 53);">动态导入</font>

<h3 id="q8PNg">多入口打包</h3>

<font style="color:rgb(53, 53, 53);">多入口打包通常用于多页面应用，但也可以一个页面应用多个bundle，实现分包</font>

<font style="color:rgb(53, 53, 53);">同事可以使用</font>`<font style="color:rgb(233, 105, 0);">dependOn</font>`<font style="color:rgb(53, 53, 53);">指定依赖的公共模块，并在html中引入公共模块</font>

**js**

```plain
entry: {
  main: {
    import: ['./index.js', './main.js'],
    dependOn: 'shared',
  },
  about: {
    import: ['./about.js'],
    dependOn: 'shared',
  },
  shared: './module.js',
},
output: {
  path: path.resolve(__dirname, 'dist'),
  filename: '[name]_[contenthash].js',
  clean: true,
},
plugins: [
  new HtmlWebpackPlugin({
    template: path.resolve(__dirname, './index.html'), // 自定义模板
    inject: 'body', // 插入到body
    filename: 'index.html', // 输出文件名，默认index.html
    title: 'webpack测试', // 自定义title，通过<%= htmlWebpackPlugin.options.title %>在html中使用
    minify: true, // 压缩
    chunks: ['main', 'shared'], // 公共模块也要引入
  }),
  new HtmlWebpackPlugin({
    template: path.resolve(__dirname, './about.html'),
    inject: 'body',
    filename: 'about.html',
    title: '关于页',
    minify: true, // 压缩
    chunks: ['about', 'shared'],
  }),
],
```

<font style="color:rgb(53, 53, 53);">如果想要在一个 HTML 页面上使用多个入口，还需设置</font><font style="color:rgb(53, 53, 53);"> </font>[<font style="color:rgb(53, 53, 53);">runtimeChunk</font>](https://webpack.docschina.org/configuration/optimization/#optimizationruntimechunk)

**js**

```plain
optimization: {
  // 用于指定运行时(runtime)代码的拆分策略
  runtimeChunk: 'single',
},
```

<h3 id="IFW6L">自动提取</h3>

<font style="color:rgb(53, 53, 53);">当多个模块引入了同一个模块，可以使用</font>[<font style="color:rgb(53, 53, 53);">splitChunks</font>](https://webpack.docschina.org/plugins/split-chunks-plugin/)<font style="color:rgb(53, 53, 53);">将其自动提取为独立的chunk</font>

**js**

```plain
splitChunks: {
  chunks: 'all',
  minSize: 20 * 1024, // 设置最小分包大小,默认20000
  minSizeReduction: 50 * 1024, // 需要分包的bundle最小大小
},
```

`<font style="color:rgb(233, 105, 0);">minSizeReduction</font>`<font style="color:rgb(53, 53, 53);">：设置需要分包的bundle最小大小，这意味着如果分割成一个 chunk 并没有减少主 chunk（bundle）的给定字节数，它将不会被分割，即使它满足 splitChunks.minSize</font>

<font style="color:rgb(53, 53, 53);">这样就不用使用</font>`<font style="color:rgb(233, 105, 0);">dependOn</font>`<font style="color:rgb(53, 53, 53);">指定依赖的公共模块了</font>

<h3 id="zBmI2">动态导入</h3>

[<font style="color:rgb(53, 53, 53);">动态导入</font>](https://webpack.docschina.org/guides/code-splitting/#dynamic-imports)<font style="color:rgb(53, 53, 53);">实现按需加载，需要某个模块再加载该模块，所有动态导入的模块都会被自动分包</font>

<font style="color:rgb(53, 53, 53);">使用ESM的</font>`<font style="color:rgb(233, 105, 0);">import()</font>`<font style="color:rgb(53, 53, 53);">实现动态导入</font>

<font style="color:rgb(53, 53, 53);">下面是一个hash路由的小demo</font>

**html**

```plain
<body>
  <header>
    <a href="#Home">首页</a>
    <a href="#List">列表</a>
  </header>
  <div id="main"></div>
</body>
```

**js**

src/blog.js

```plain
import home from './home';
import list from './list';

const render = ()=>{
  const hash = window.location.hash || "#Home";
  const mainEle = document.querySelector('#main');
  mainEle.innerHTML = "";
  if(hash === "#List"){
    mainEle.appendChild(list());
  }else if(hash === "#Home"){
    mainEle.appendChild(home());
  }
}
render();

window.addEventListener("hashchange", render)
```

**js**

src/home/index.js

```plain
import { renderMarkdown } from "../module";
import './index.css'
import md from './index.md'
export default () => renderMarkdown(md, "home");
```

**js**

src/list/index.js

```plain
import { renderMarkdown } from "../module";
import './index.css'
import md from './index.md'
export default () => renderMarkdown(md, 'list');
```

<font style="color:rgb(53, 53, 53);">若不使用动态导入，不同路由页引入的css都同时影响样式，导致样式冲突，下面使用</font>`<font style="color:rgb(233, 105, 0);">import()</font>`<font style="color:rgb(53, 53, 53);">改造</font>

**js**

src/blog.js

```plain
const render = () => {
  const hash = window.location.hash || "#Home";
  const mainEle = document.querySelector('#main');
  mainEle.innerHTML = "";
  if (hash === "#List") {
    import('./list').then(({ default: list }) => {
      mainEle.appendChild(list());
    })
  } else if (hash === "#Home") {
    import('./home').then(({ default: home }) => {
      mainEle.appendChild(home());
    })
  }
}
render();

window.addEventListener("hashchange", render)
```

<h3 id="Y3ON1">魔法注释</h3>

<font style="color:rgb(53, 53, 53);">在动态导入过程中可以加入魔法注释，控制分包命名、合并、开启</font>[<font style="color:rgb(53, 53, 53);">预加载</font>](https://webpack.docschina.org/guides/code-splitting/#prefetchingpreloading-modules)

**js**

```plain
// 使用chunkName设置分包命名
import(/* webpackChunkName: "home" */'./home')
import(/* webpackChunkName: "list" */'./list')
// 相同chunkName会被打包到一起
import(/* webpackChunkName: "components" */'./home')
import(/* webpackChunkName: "components" */'./list')
// 开启预加载
import(/* webpackPrefetch: true */'./list');
```

<h1 id="XjBRY">css处理进阶</h1>

<font style="color:rgb(53, 53, 53);">css这东西吧，还得琢磨琢磨</font>

<h2 id="ijIJ0">css-loader模块化</h2>

<font style="color:rgb(53, 53, 53);">开启</font>`<font style="color:rgb(233, 105, 0);">options.modules</font>`<font style="color:rgb(53, 53, 53);">，css-loader会将样式中的类名进行转换，根据模块路径和类名生成转换为一个唯一的hash值。</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/loaders/css-loader/#modules)

**<font style="color:rgb(53, 53, 53);">作用：</font>**<font style="color:rgb(53, 53, 53);">CSS的规则都是全局的，任何一个组件的样式规则，都对整个页面有效。产生局部作用域的唯一方法，就是使用一个独一无二的class的名字，不会与其他选择器重名</font>

**js**

```plain
rules: [
  {
    test: /\.css$/i,
    loader: "css-loader",
    options: {
      modules: true,
    },
  },
],
```

<font style="color:rgb(53, 53, 53);">通过导出对象访问类名来应用样式</font>

**css**

```plain
.list{
  background-color: #2f59b4
}
```

**js**

```plain
import { renderMarkdown } from "../module";
import css from './index.css'
import md from './index.md'
export default () => renderMarkdown(md, css.list);
```

<h2 id="ROK4P">提取css</h2>

<font style="color:rgb(53, 53, 53);">之前css通过style-loader直接应用到style标签内，而css则保存在js模块中，若css体积较大，还是提取css为一个单独的文件好</font>

[<font style="color:rgb(53, 53, 53);">MiniCssExtractPlugin</font>](https://webpack.docschina.org/plugins/mini-css-extract-plugin/)<font style="color:rgb(53, 53, 53);">将 CSS 提取到单独的文件中，为每个包含 CSS 的 JS 文件创建一个 CSS 文件，并且支持 CSS 和 SourceMaps 的按需加载</font>

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i mini-css-extract-plugin -D</font>`

**js**

配置

```plain
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  plugins: [new MiniCssExtractPlugin()],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: [MiniCssExtractPlugin.loader, "css-loader"],
      },
    ],
  },
};
```

<h2 id="mlkJ3">压缩css</h2>

<font style="color:rgb(53, 53, 53);">webpack本身只能压缩JS模块,需要压缩CSS等其它类型文件需要安装对应的插件</font>

<font style="color:rgb(53, 53, 53);">使用</font>[<font style="color:rgb(53, 53, 53);">CssMinimizerWebpackPlugin</font>](https://webpack.docschina.org/plugins/css-minimizer-webpack-plugin/)<font style="color:rgb(53, 53, 53);">优化和压缩独立的CSS模块</font>

<font style="color:rgb(53, 53, 53);">安装：</font>`<font style="color:rgb(233, 105, 0);">npm i css-minimizer-webpack-plugin -D</font>`

**js**

配置

```plain
const CssMinimizerPlugin = require("css-minimizer-webpack-plugin");

optimization: {
  minimize: true,
  // 压缩类的插件应配置在minimizer，受minimize控制
  minimizer: [
    // 在 webpack@5 中，你可以使用 `...` 语法来扩展现有的 minimizer（即 `terser-webpack-plugin`）
    `...`,
    new CssMinimizerPlugin(),
  ],
},
```

<h1 id="jiFAz">文件hash</h1>

<font style="color:rgb(53, 53, 53);">开启静态资源的客户端缓存后，为了能及时更新资源，资源文件就需要带上hash，</font>[<font style="color:rgb(53, 53, 53);">文档</font>](https://webpack.docschina.org/guides/caching/)

<font style="color:rgb(53, 53, 53);">绝大多数插件都支持使用</font>`<font style="color:rgb(233, 105, 0);">filename</font>`<font style="color:rgb(53, 53, 53);">配置输出的文件名</font>

<font style="color:rgb(53, 53, 53);">三种hash：</font>

**js**

```plain
// [hash]项目级hash，项目中一个模块有变化，该hash就变化
filename: '[name]_[hash].js',
// [chunkhash]chunk级hash，同一路的打包相同hash
filename: '[name]_[chunkhash].js',
// [contenthash]文件级hash，根据输出文件内容的hash
filename: '[name]_[contenthash].js',
```

<font style="color:rgb(53, 53, 53);">指定hash长度</font>

**js**

```plain
filename: '[name]_[contenthash:8].js',
```

<font style="color:rgb(53, 53, 53);">控制缓存最佳实践：8位contenthash</font>

<h1 id="hC4TN">总结</h1>

**json**

package.json

```plain
{
  "name": "webpack01",
  "version": "1.0.0",
  "description": "",
  "private": true,
  "scripts": {
    "build": "webpack --config webpack.prod.js",
    "build-dev": "webpack --config webpack.dev.js",
    "prod": "webpack serve --config webpack.prod.js",
    "dev": "webpack serve --config webpack.dev.js"
  },
  "sideEffects": [
    "*.css",
    "./src/pad.js"
  ],
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/core": "^7.23.3",
    "@babel/preset-env": "^7.23.3",
    "babel-loader": "^8.3.0",
    "copy-webpack-plugin": "^11.0.0",
    "css-loader": "^6.8.1",
    "css-minimizer-webpack-plugin": "^5.0.1",
    "file-loader": "^6.2.0",
    "html-loader": "^4.2.0",
    "html-webpack-plugin": "^5.5.3",
    "marked": "^9.1.6",
    "mini-css-extract-plugin": "^2.7.6",
    "style-loader": "^3.3.3",
    "url-loader": "^4.1.1",
    "webpack": "^5.74.0",
    "webpack-bundle-analyzer": "^4.9.1",
    "webpack-cli": "^4.10.0",
    "webpack-dev-server": "^4.15.1",
    "webpack-merge": "^5.10.0"
  }
}
```

<h1 id="VmFlU">配置TS环境</h1>

<font style="color:rgb(53, 53, 53);">安装TS相关依赖：</font>

1. <font style="color:rgb(53, 53, 53);">编译TS</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">npm install ts-loader -D</font>`
2. <font style="color:rgb(53, 53, 53);">TS环境</font><font style="color:rgb(53, 53, 53);"> </font>`<font style="color:rgb(233, 105, 0);">npm install typescript -D</font>`

**js**

配置webpack.config.js

```plain
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack');
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
const CssMinimizerPlugin = require("css-minimizer-webpack-plugin");

module.exports = {
  mode: 'none',
  // 生成源映射以方便调试
  devtool: 'source-map',
  // watch: true,
  context: path.resolve(__dirname, 'src'),
  entry: {
    main: {
      import: ['./index.ts'],
    }
  },
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name]_[contenthash].js',
    clean: true,
  },
  optimization: {
    usedExports: true,
    // minimize: true,
    // 用于指定运行时(runtime)代码的拆分策略
    // runtimeChunk: 'single',
    // splitChunks: {
    //   chunks: 'all',
    //   minSize: 10 * 1024, // 设置最小分包大小
    //   // minSizeReduction: 50 * 1024, // 需要分包的bundle最小大小
    // },
    minimizer: [
      // 在 webpack@5 中，你可以使用 `...` 语法来扩展现有的 minimizer（即 `terser-webpack-plugin`）
      `...`,
      new CssMinimizerPlugin(),
    ],
  },
  //警告 webpack 的性能提示
  performance: {
    hints: 'warning',
    //入口起点的最大体积
    maxEntrypointSize: 1024 * 1024 * 10,
    //生成文件的最大体积
    maxAssetSize: 1024 * 1024,
    //只给出 js 文件的性能提示
    assetFilter: function (assetFilename) {
      return /\.ts$/.test(assetFilename);
    }
  },
  module: {
    rules: [
      {
        // 正则匹配loader要处理的资源
        test: /\.css$/i,
        // 逆序执行，从右往左
        use: [
          // {
          //   loader: 'style-loader',
          // },
          {
            loader: MiniCssExtractPlugin.loader
          },
          {
            loader: 'css-loader',
            // options: {
            //   modules: true // css-loader会将样式中的类名进行转换，根据模块路径和类名生成转换为一个唯一的hash值。
            // },
          },
        ],
      },
      {
        test: /\.(png|jpg|svg|gif|ico)$/,
        type: "asset",
        generator: {
          filename: "img/[name]_[contenthash][ext]",
        },
        parser: {
          dataUrlCondition: {
            maxSize: 50 * 1024,//小于50kb进行编码，转为base64
          },
        },
      },
      {
        test: /\.js$/i,
        include: [
          path.resolve(__dirname, 'src')
        ],
        exclude: [
          path.resolve(__dirname, 'node_modules')
        ],
        loader: 'babel-loader',
        options: {
          presets: ["@babel/preset-env"]
          // presets: [
          //   ["@babel/preset-env", {
          //     modules: "commonjs", // 开启ESM转CommonJS
          //   }]
          // ]
        }
      },
      {
        test: /\.ts$/i,
        loader: "ts-loader",
        include: [
          path.resolve(__dirname, 'src')
        ],
        exclude: [
          path.resolve(__dirname, 'node_modules')
        ],
      }
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, './index.html'), // 自定义模板
      inject: 'body', // 插入到body
      filename: 'index.html', // 输出文件名，默认index.html
      title: 'webpack测试', // 自定义title，通过<%= htmlWebpackPlugin.options.title %>在html中使用
      minify: true, // 压缩
      chunks: ['main'],
    }),
    new webpack.DefinePlugin({
      API_BASE_URL: JSON.stringify('http://api.github.com'),
    }),
    new MiniCssExtractPlugin(),
  ],
  resolve: {
    extensions: ['.ts', '.js'],
    alias: {
      '@': path.resolve(__dirname, './src')
    }
  },
  // 配置开发服务器
  devServer: {
    // 服务器主机
    host: 'localhost',
    // 服务器端口
    port: 8080,
    // 使用HMR
    hot: true,
    // 启用Gzip
    compress: true,
    // CopyPlugin通常只在项目上线时去使用，开发时通常将静态资源目录配置给devServer，以提高性能
    // 使用static配置从目录提供静态文件的选项，默认public
    static: {
      // 告诉服务器从哪里提供内容
      directory: path.join(__dirname, 'public'),
    },
    proxy: {
      // 代理api路径
      '/api': {
        // localhost:8080/api/user -> api.github.com/api/user
        target: 'https://api.github.com',
        // 请求路径重写 /api/user -> /user
        pathRewrite: { '^/api': '' },
        // 将 host 请求头修改为 target 的 URL
        changeOrigin: true,
      },
    },
  }
}
```

**json**

tsconfig.json

```plain
{
  "compilerOptions": {
    "incremental": false, // TS编译器在第一次编译之后会生成一个存储编译信息的文件，第二次编译会在第一次的基础上进行增量编译，可以提高编译的速度
    // "tsBuildInfoFile": "./buildFile", // 增量编译文件的存储位置
    "diagnostics": true, // 打印诊断信息 
    "target": "esnext", /* 指定 ECMAScript 目标版本：'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017','ES2018' or 'ESNEXT'. */
    "module": "esnext", /* 输出的代码使用什么方式进行模块化： 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. */
    "lib": [ /* 指定引用的标准库 */
      "esnext",
      "dom",
      "dom.iterable",
    ], // TS需要引用的库，即声明文件，es5 默认引用dom、es5、scripthost,如需要使用es的高级版本特性，通常都需要配置，如es8的数组新特性需要引入"ES2019.Array",
    "allowJs": true, // 允许编译器编译JS，JSX文件
    "checkJs": true, // 允许在JS文件中报错，通常与allowJS一起使用
    "outDir": "./dist", // 指定输出目录
    "rootDir": "./src", // 指定输出文件目录(用于输出)，用于控制输出目录结构
    "declaration": true, // 生成声明文件，开启后会自动生成声明文件
    "declarationDir": "./dist/typings", // 指定生成声明文件存放目录
    // "emitDeclarationOnly": true, // 只生成声明文件，而不会生成js文件
    "sourceMap": false, // 生成目标文件的sourceMap文件
    // "inlineSourceMap": true, // 生成目标文件的inline SourceMap，inline SourceMap会包含在生成的js文件中
    "declarationMap": false, // 为声明文件生成sourceMap
    // "typeRoots": [], // 声明文件目录，默认时node_modules/@types
    "types": [], // 加载的声明文件包
    "removeComments": true, // 删除注释 
    "noEmit": false, // 不输出文件,即编译后不会生成任何js文件
    "noEmitOnError": true, // 发送错误时不输出任何文件
    "noEmitHelpers": true, // 不生成helper函数，减小体积，需要额外安装，常配合importHelpers一起使用
    "importHelpers": true, // 通过tslib引入helper函数，文件必须是模块
    "downlevelIteration": true, // 降级遍历器实现，如果目标源是es3/5，那么遍历器会有降级的实现
    "strict": true, // 开启所有严格的类型检查
    "alwaysStrict": true, // 在代码中注入'use strict'
    "noImplicitAny": true, // 不允许隐式的any类型
    "strictNullChecks": true, // 不允许把null、undefined赋值给其他类型的变量
    "strictFunctionTypes": true, // 不允许函数参数双向协变
    "strictPropertyInitialization": true, // 类的实例属性必须初始化
    "strictBindCallApply": true, // 严格的bind/call/apply检查
    "noImplicitThis": true, // 不允许this有隐式的any类型
    "noUnusedLocals": true, // 检查只声明、未使用的局部变量(只提示不报错)
    "noUnusedParameters": true, // 检查未使用的函数参数(只提示不报错)
    "noFallthroughCasesInSwitch": true, // 防止switch语句贯穿(即如果没有break语句后面不会执行)
    "noImplicitReturns": true, //每个分支都会有返回值
    "esModuleInterop": true, // 允许export=导出，由import from 导入
    "allowUmdGlobalAccess": true, // 允许在模块中全局变量的方式访问umd模块
    "moduleResolution": "node", // 模块解析策略，ts默认用node的解析策略，即相对的方式导入
    "baseUrl": "./", // 解析非相对模块的基地址，默认是当前目录
    "paths": { // 路径映射，相对于baseUrl
      // 如使用jq时不想使用默认版本，而需要手动指定版本，可进行如下配置
      // "jquery": [
      //   "node_modules/jquery/dist/jquery.min.js"
      // ],
      "@/*": [
        "src/*"
      ]
    },
    "rootDirs": [
      "src"
    ], // 将多个目录放在一个虚拟目录下，用于运行时，即编译后引入文件的位置可能发生变化，这也设置可以虚拟src和out在同一个目录下，不用再去改变路径也不会报错
    "listEmittedFiles": true, // 打印输出文件
    "listFiles": true, // 打印编译的文件(包括引用的声明文件)
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,
    "resolveJsonModule": true,
    "allowImportingTsExtensions": true,
  },
  // 指定一个匹配列表（属于自动指定该路径下的所有ts相关文件）
  "include": [
    "src/**/*",
  ],
  // 指定一个排除列表（include的反向操作）
  // "exclude": [
  //   "demo.ts"
  // ],
  // 指定哪些文件使用该配置（属于手动一个个指定文件）
  // "files": [
  //   "demo.ts"
  // ]
}
```

