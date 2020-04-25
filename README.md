# monaco-vue-demo
此项目在monaco-editor官方文档的基础上，演示在vue-cli4新建的项目如何以webpack的方式集成monaco编辑器。

## 项目运行
```
npm install
```

```
npm run dev
```

## 原理
[monaco-editor官方webpack集成指引1](https://github.com/Microsoft/monaco-editor/blob/HEAD/docs/integrate-esm.md#option-1-using-the-monaco-editor-loader-plugin)已经给出了webpack集成monaco-editor的方法了。然后结合[vue-cli配置webpack](https://cli.vuejs.org/zh/guide/webpack.html#%E7%AE%80%E5%8D%95%E7%9A%84%E9%85%8D%E7%BD%AE%E6%96%B9%E5%BC%8F)的方法，vue集成monaco-editor的方法就出来了。

在vue.config.js添加monaco-editor-webpack-plugin
```
const MonacoWebpackPlugin = require('monaco-editor-webpack-plugin')

module.exports = {
  configureWebpack: {
    plugins: [
      new MonacoWebpackPlugin()
    ]
  }
}
``` 
然后在需要的地方使用就行了，比如App.vue中
```
import * as monaco from "monaco-editor";

monaco.editor.create(document.getElementById("app"), {
      value: [
        "function x() {",
        '\tconsole.log("Hello world!");',
        "}"].join(
        "\n"
      ),
      language: "javascript",
      theme: 'vs-dark',
      automaticLayout: true
    });
```
注意要给monaco编辑器所在的元设置样式，指定宽高。


