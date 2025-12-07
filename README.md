# basicWebpackPractice

# restaurant-Page

### setup webpack

- `npm init -y`
- `mkdir src`
- `mkdir dist`

- add basic webpack plugins 
```bash
npm install --save-dev webpack webpack-cli
```
```bash
npm install --save-dev html-webpack-plugin
```
```bash
npm install --save-dev style-loader css-loader
```
```bash
npm install --save-dev html-loader
```
```bash
npm install --save-dev webpack-dev-server
```
add the plugin/module config `in webpack.config.js`
```js

// webpack.config.js
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
  },
  devtool: "eval-source-map",
  devServer: {
    watchFiles: ["./src/template.html"],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/template.html",
    }),
  ],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.html$/i,
        loader: "html-loader",
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      }
    ],
  },
};
```
```bash
touch /src/index.js
touch /src/template.html
touch /src/styles.css
```
- add html boilerplate
### start live preview 
``` bash
npx webpack serve
```
access page here [http://localhost:8080/](http://localhost:8080/)
