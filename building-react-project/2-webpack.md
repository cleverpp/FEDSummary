## 基础配置，让React运行起来
entry：入口文件

output：打包后的文件输出

loader：如何处理资源文件，例如我们使用es6，则需要babel-loader来解析js或jsx等。

plugins：处理各种特定的任务，例如生产环境，我们需要将文件压缩混淆，这个任务通过plugins来处理。

webpack.config.js

```
const path = require('path');
const root = __dirname;
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin'); //installed via npm

module.exports = {
    entry: path.resolve(root, 'src/main.js'),
    output: {
        filename: 'bundle.js',
        path: path.resolve(root, 'dist')
    },
    module: {
        rules: [
            {test: /\.jsx?$/, use: 'babel-loader', exclude: /node_modules/}
        ]
    },
    plugins:[
        new webpack.optimize.UglifyJsPlugin(),
        new HtmlWebpackPlugin({
            template: 'index.html'
        })
    ]
}
```
## 热加载
## 代码分离code spliting
webpack支持代码分离的历史发展，例如require.ensure()，dynamic import()
