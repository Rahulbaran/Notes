# [WEBPACK] (https://webpack.js.org/concepts/)

- It is a module bundler.

- Some other module bundlers are **Parcel, Rollup** etc.

- **webpack** figures out dependencies using **dependency graph**.

- There are following main concepts when getting started with **webpack**.

  1. entry
  2. output
  3. mode
  4. Loaders
  5. plugins

---

### 1. entry

- **context** property is used in the configuration object to mention the **absolute path** of the folder where all the entry files are.

### 2. output

- The location where we want our bundled files.

- We use **output** property which can take either a string containing output folder location or an object containing a bunch of optional properties(filename, path, clean etc.)

- **path** property is used to mention the folder where we want our **bundled** modules.

- **filename** property is used for mentioning the bundled filename.

- **clean** property is used to empty **dist** folder before generating new one.

- **[main]** uses **main** property of **entry point** as prefix in bundled file.

- **[contenthash]** generates new hash value each time we run **webpack**, which can be used for generating new bundle files.

- **[hash]**, **[chunkhash]** & **[contenthash]** all are different and Their differences can be visualize when having more than one file in **entry** property.

```js
const path = require("path");

module.exports = {
  entry: {
    main: "./script.js"
  },
  context: path.resolve(__dirname, "src"),
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "[main].[contenthash].js",
    clean: true
  }
};
```

### 3. mode

- Used to mention application mode which is either **development** or **production**.

- Default mode is **production**.

- Options are **development**, **production** & **none**.

```js
module.exports = {
  entry: {
    main: path.resolve(__dirname, "src/script.js"),
  },
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "[main].[contenthash].js",
    clean: true
  }
 mode: "development"
};
```

### 4. Loaders

- By default, **webpack** only understands **js** & **json** files.

- To process other files like **css, images, html, text, csv** etc we use **Loaders**.

- **module.rules** property is used to mention **Loaders**.

- **Loaders** can be chained and they are executed in reverse order.

- They can be synchronous or asynchronous.

- **Plugins** provide more features to **Loaders**.

```js
const path = require("path");

module.exports = {
  context: path.resolve(__dirname, "src"),
  entry: { main: "./script.js" },
  mode: "development",

  ouput: {
    path: path.resolve(__dirname, "dist"),
    filename: "[main].[contenthash].js",
    clean: true
  },

  module: {
    rules: [
      { test: /\.css$/, use: ["css-loader", "style-loader"] },
      { test: /\.txt$/, use: "raw-loader" }
    ]
  }
};
```

- `css-loader` finds the **CSS** files and converts them into **CSS Modules**.
- `style-loader` injects **CSS Modules** in bundled javascript file.

- `mini-css-extract-plugin` is used to generate a new **CSS** file instead of injecting it in bundled js file. (don't use `style-loader`)

### 5. plugins

- While **loaders** are used to transform certain types of modules, **plugins** can be leveraged to perform a wider range of tasks like **bundle optimization, asset management and injection of environment variables**.

- **Example** - "html-webpack-plugin" for generating a html file in **dist** folder & injecting all the bundle files.

- We use **plugins** property to mention plugins in form of an array.

-

```js
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  plugins: [
    new HtmlWebpackPlugin({
      title: "Webpack Concept",
      filename: "index.html",
      template: path.resolve(__dirname, "src/index.html")
    })
  ]
};
```

---

- `webpack-dev-server` is used to serve files generated using **Webpack**.

##### Configuration for serving files :-

```js
const path = require("path");

module.exports = {
  devtool: "inline-source-map", //source-map
  devServer: {
    static: path.resolve(__dirname, "dist"),
    open: true,
    hot: true,
    port: 5050,
    server: "http"
  }
};
```

- **devtool** property controls how source maps are generated. There are a bunch of values which we can use for this property. Recommended value for development is `eval-source-map` & for production it is `source-map`. Other values are `inline-source-map`, `cheap-source-map`, `eval`.
