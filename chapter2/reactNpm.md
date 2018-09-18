## webpack配置react
**1. 初始化package.json**

`npm init`

**2. 安装babel-loader(新版8.0.0报错)**

`cnpm install babel-loader@7.1.5 babel-preset-es2015 babel-preset-react --save-dev`

**3. 安装webpack**

`cnpm install webpack webpack-cli webpack-dev-server --save-dev`

**4. 创建webpack.config.js**

```javascript
var path = require('path');
var webpack = require('webpack');
var HtmlwebpackPlugin = require('html-webpack-plugin');

var ROOT_PATH = path.resolve(__dirname);
var APP_PATH = path.resolve(ROOT_PATH, 'app');
var BUILD_PATH = path.resolve(ROOT_PATH, 'build');

module.exports= {
    entry: {
        app: path.resolve(APP_PATH, 'index.jsx')
    },
    output: {
        path: BUILD_PATH,
        filename: 'bundle.js'
    },
    mode: "development",
    // mode: "production",
    //enable dev source map
    devtool: 'eval-source-map',
    //enable dev server
    devServer: {
        historyApiFallback: true,
        hot: true,
        inline: true,
        progress: true,
        port: 3000
    },
    //babel重要的loader在这里
    module: {
        rules: [
            {
                test: /\.jsx?$/,
                loader: 'babel-loader',
                include: APP_PATH
            },
            {
                test: /\.scss$/,
                loaders: ['style-loader', 'css-loader', 'sass-loader']
            },
			{
				test: /\.(png|jpg|gif|svg)$/,
				loader: 'file-loader',
				options: {
					name: '[name].[ext]?[hash]'
				}
			},
			{ 
				test: /\.(gif|jpg|png|woff|woff2|svg|eot|ttf)\??.*$/, 
				loader: 'url-loader?limit=50000&name=[path][name].[ext]'
			}
        ]
    },
    resolve: {
        extensions: ['*', '.js', '.jsx']
    },
    plugins: [
        new HtmlwebpackPlugin({
            title: 'My first react app',
            template: "index.html",
            filename: "index.html",
            inject: true
        })
    ]
}
```

**5. npm中添加webpack启动命令**

```javascript
    "dev": "webpack-dev-server --progress --profile --colors --hot",
    "build": "webpack --progress --profile --colors",
    "test": "karma start"
```

**6. 安装React和React-Dom**

`cnpm install react react-dom --save`

**7. 应用中使用sass**

`cnpm install css-loader style-loader sass-loader node-sass --save-dev`

**8. 创建 .babelrc文件，babel分离**

```javascript
{
    "presets": ["react", "es2015"],
    "env": {
        "development": {
            "presets": ["react-hmre"]
        }
    }
}
```

**9. 安装其他loader**

`cnpm install html-webpack-plugin file-loader babel-core url-loader babel-preset-react-hmre --save-dev`

**10. loader汇总**

```javascript
"devDependencies": {
    "babel-core": "^6.26.3",
    "babel-loader": "^7.1.5",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "babel-preset-react-hmre": "^1.1.1",
    "css-loader": "^1.0.0",
    "file-loader": "^2.0.0",
    "html-webpack-plugin": "^3.2.0",
    "node-sass": "^4.9.3",
    "sass-loader": "^7.1.0",
    "style-loader": "^0.23.0",
    "url-loader": "^1.1.1",
    "webpack": "^4.17.1",
    "webpack-cli": "^3.1.0",
    "webpack-dev-server": "^3.1.7"
  },
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2"
  }
```