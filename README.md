# AntDesign

## 配置Webpack步骤:
### 1、npm init -y //初始化
### 2、npm install --save-dev webpack
### 3、创建webpack config文件: webpack.config.js

const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  }
};

---修改package.json,添加以下代码
"scripts": {
    "build": "webpack"
},

### 4、接下来配置Babel

npm install --save-dev babel-loader babel-core
在Webpackage.config.js里添加
  module: {
    rules: [
      { test: /\.js$/, exclude: /node_modules/, loader: "babel-loader" }
    ]
  }
创建.babelrc文件
npm install --save-dev babel-preset-env
npm install --save-dev babel-preset-react
在里边添加
{
  "presets": ["env", "react"]
}

### 5、添加React

npm install --save react react-dom

---至此，React环境配置完成

### 6、CSS In JavaScript 配置

npm install --save-dev style-loader css-loader
---
在webpack.config.js中添加

module: {
  rules: [
    {
      test: /\.css$/,
      use: [
        'style-loader',
        'css-loader'
      ]
    }
  ]
}

### 7、less配置

npm install --save-dev less-loader less

module: {
        rules: [{
            test: /\.less$/,
            use: [{
                loader: "style-loader" // creates style nodes from JS strings
            }, {
                loader: "css-loader" // translates CSS into CommonJS
            }, {
                loader: "less-loader" // compiles Less to CSS
            }]
        }]
    }

### 配置开发者模式

在webpack.config.js里添加
devtool: 'inline-source-map',

#### watch mode配置

package.json
 "watch": "webpack --watch",

 npm install --save-dev webpack-dev-server

 webpack.config.js
 devServer: {
   contentBase: './dist'
 },



