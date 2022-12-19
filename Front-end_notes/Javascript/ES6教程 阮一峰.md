# ES6 前言
## Babel 转码器
[Babel](https://babeljs.io/) 是一个广泛使用的 ES6 转码器，可以将 ES6 代码转为 ES5 代码，从而在老版本的浏览器执行。

### 配置文件`.babelrc`
Babel 的配置文件是`.babelrc`，存放在项目的根目录下。使用 Babel 的第一步，就是配置这个文件。
该文件用来设置转码规则和插件，基本格式如下。
``` json
{
  "presets": [],
  "plugins": []
}
```

`presets`字段设定转码规则，官方提供以下的规则集，你可以根据需要安装。
``` bash
# 最新转码规则
$ npm install --save-dev @babel/preset-env

# react 转码规则
$ npm install --save-dev @babel/preset-react
```

然后，将这些规则加入`.babelrc`。
```json
  {
    "presets": [
      "@babel/env",
      "@babel/preset-react"
    ],
    "plugins": []
  }
```
注意，以下所有 Babel 工具和模块的使用，都必须先写好`.babelrc`。

### polyfill
Babel 默认只转换新的 JavaScript 句法（syntax），而不转换新的 API，比如`Iterator`、`Generator`、`Set`、`Map`、`Proxy`、`Reflect`、`Symbol`、`Promise`等全局对象，以及一些定义在全局对象上的方法（比如`Object.assign`）都不会转码。

举例来说，ES6 在`Array`对象上新增了`Array.from`方法。Babel 就不会转码这个方法。如果想让这个方法运行，可以使用`core-js`和`regenerator-runtime`(后者提供generator函数的转码)，为当前环境提供一个垫片。

安装命令如下。
``` bash
$ npm install --save-dev core-js regenerator-runtime
```

然后，在脚本头部，加入如下两行代码。
``` js
import 'core-js';
import 'regenerator-runtime/runtime';
// 或者
require('core-js');
require('regenerator-runtime/runtime');
```

Babel 默认不转码的 API 非常多，详细清单可以查看`babel-plugin-transform-runtime`模块的[definitions.js](https://github.com/babel/babel/blob/master/packages/babel-plugin-transform-runtime/src/runtime-corejs3-definitions.js)文件。


```dataviewjs
function projectTracker(dv, query) {
    let searchPagePaths = dv.pages(query).file.path
    
    for(let i=0; i < searchPagePaths.length; i++){
        if(dv.page(searchPagePaths[i]).Total){
                    let title = dv.page(searchPagePaths[i]).Title;
                    let total = dv.page(searchPagePaths[i]).Total;
                    let status = ((dv.page(searchPagePaths[i]).Completed / dv.page(searchPagePaths[i]).Total) * 100).toFixed();
                    let suffix = dv.page(searchPagePaths[i]).Suffix;
                    const progress = "![pb|500](https://progress-bar.dev/" + status + "/?scale=" + "100" + "&title=" + title + "&width=400)";
                    dv.paragraph(progress);
                    dv.paragraph("<br>");
        }
    }
} 

projectTracker(
    dv,
    "#projects"
)
```
