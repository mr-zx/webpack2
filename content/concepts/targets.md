---
title: 部署目标
sort: 10
contributors:
  - TheLarkInn
  - dear-lizhihua
---

因为服务器和浏览器代码都可以用 JavaScript 编写，所以 webpack 提供了多种部署_目标(target)_，你可以在你的 webpack [配置](/configuration)中设置。

W> webpack `target` 属性不要和 `output.libraryTarget` 属性混淆。有关 `output` 属性的更多信息，请查看[我们的指南](/concepts/output)。

## 用法

要设置 `target` 属性，只需要在你的 webpack 配置中设置 target 的值。

**webpack.config.js**

```javascript
module.exports = {
  target: 'node'
};
```

每个_目标_都有各种部署/环境特定的附加项，以支持满足其需求。查看[可用目标](/configuration/target)。
Each _target_ has a variety of deployment/environment specific additions, support to fit its needs. See what [targets are available](/configuration/target).

?> We should expand on this further. What specifically is included.

## 多个目标

尽管 webpack 不支持向 `target` 传入多个字符串，你可以通过打包两份分离的配置来创建同构的库：

**webpack.config.js**

```javascript
var serverConfig = {
  target: 'node',
  output: {
    path: 'dist',
    filename: 'lib.node.js'
  }
  //…
};

var clientConfig = {
  target: 'web', // <=== 默认是 'web'，可省略
  output: {
    path: 'dist',
    filename: 'lib.js'
  }
  //…
};

module.exports = [ serverConfig, clientConfig ];
```

上面的例子将在你的 `dist` 文件夹下创建 `lib.js` 和 `lib.node.js` 文件。

## 资源

从上面的选项可以看出有多个不同的部署_目标_可供选择。下面是一个示例列表，以及你可以参考的资源。

### 打包输出比较

  **[compare-webpack-target-bundles](https://github.com/TheLarkInn/compare-webpack-target-bundles)**：大量有关「测试和查看不同的 webpack _目标_」的资源。也有大量 bug 报告。

?> Need to find up to date examples of these webpack targets being used in live code or boilerplates.

***

> 原文：https://webpack.js.org/concepts/targets/