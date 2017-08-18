[View version without answers](https://github.com/styopdev/webpack-interview-questions/blob/master/README.md)

## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Development](#development)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced-questions](#advanced-questions)

### Concepts

***Question:*** What is webpack? 

***Answer:*** webpack is a module bundler for javascript applications. Webpack recursively builds every module in your application, then packages all of those modules into a small number of bundles.
  
***Question:*** What is the main difference between webpack and other build tools like gulp or grunt?

***Answer:*** Webpack is a module bundler, though it is quite often used instead of Gulp or Grunt task runners. This advanced tool provides developers with control over how it splits the modules, allowing them to adjust builds to particular situations and workaround solutions that don’t function properly out of the box. 
  
  Comparing Webpack vs Grunt, the first of those offers more flexibility and advanced functionality for modern front-end projects. It comes with a functional core and can be extended using particular loaders and plugins. Essentially it is used for bundling JavaScript modules with dependencies into files, but for complex JavaScript applications with lots of non-code assets (images, fonts, CSS, etc.) it can provide great benefits.
  
  Talking about Webpack vs Gulp vs Grunt performance, the two latter look into a defined path for files that match your configuration, while the Webpack analyzes the whole project. It looks through all the dependencies, processes them with loaders and produces a bundled JS file. ([source](https://da-14.com/blog/gulp-vs-grunt-vs-webpack-comparison-build-tools-task-runners))

***Question:*** What is bundle in webpack?

***Answer:***

***Question:*** In which environment webpack works?

***Answer:*** node.js
  
***Question:*** What is `entry` point?

***Answer:*** The entry object is where webpack looks to start building the bundle, at this point the application starts executing.
  
***Question:*** What is dependency graph and how webpack builds it?

***Answer:*** Any time one file depends on another, webpack treats this as a dependency. Starting from entry point(s), webpack recursively builds a dependency graph that includes every module your application needs, using `import` and `require` statements, then packages all of those modules into bundle(s).


### Config file
***Question:*** What is the format of webpack's config file.
  
***Answer:*** webpack's config file is javascript file in commonjs module pattern.

***Question:*** Is it possible to have multiple entry points in singe webpack configuration file?
  
***Answer:*** Yes
  
***Question:*** Is it possible to define multiple configurations for different environments?

***Answer:*** Yes



### Loaders

***Question:*** What is loader in webpack
  
***Answer:*** Loaders are transformations that are applied on the source code of a module. webpack supports modules written in a variety of languages and preprocessors, via loaders. Loaders describe to webpack how to process non-javaScript modules and include these dependencies into your bundles.

***Question*** Where loaders should be defined?

***Answer*** in the config's object's rules property

***Question*** Explain this code

```javascript
    {
      test: /\.scss$/,
      loaders: ['style-loader', 'css-loader?sourceMap', 'sass-loader?sourceMap', 'postcss-loader'],
      exclude: /node_modules/
    }
```
    
***Answer*** 

***Question:*** Do loaders work in synchronous or asynchronous way?
  
***Answer:*** Both. Loaders can work synchronous or asynchronous.

***Question:*** Is it possible to use multiple loaders in `rules` single object?
  
***Answer:*** Yes, its possible to chain loaders.

***Question:*** Name loaders you think are very important and helpful

***Answer:*** raw-loader, url-loader, html-loader, file-loader, style-loader, css-loader, script-loader, babel-loader, loaders for typescript, coffescript, less, sass, pug, markdown, etc.

### Plugins

***Question:*** Describe plugin in webpack

***Answer:*** Plugins used to customize webpack’s build process in a variety of ways. A webpack plugin is a JavaScript object that has an apply property. This apply property is called by the webpack compiler, giving access to the entire compilation lifecycle. Webpack comes with a multiple built-in plugins available under `webpack.[plugin-name]`

***Question:*** What is difference between loader and plugin

***Answer:*** https://stackoverflow.com/a/38281240/3283209

***Question:*** What is advantage of CompressionPlugin?

***Answer:*** CompressionPlugin builds gzip-ed version of bundles. Its possible to simply add server side compression e.g using nginx or expres compression plugin. Server-side compression is not recommended because it addes load on CPU and increases response time.

***Question:*** How to move some data (e.g css code) from bundle to separate file in webpack?

***Answer:*** using ExtractTextWebpackPlugin. It moves all the required *.css modules in entry chunks into a separate CSS file. So your styles are no longer inlined into the JS bundle, but in a separate CSS file (styles.css). If your total stylesheet volume is big, it will be faster because the CSS bundle is loaded in parallel to the JS bundle. 
https://github.com/webpack-contrib/extract-text-webpack-plugin

***Question:*** Name plugins you think are very important and helpful

***Answer:*** CommonsChunkPlugin, DefinePlugin, HtmlWebpackPlugin, ExtractTextWebpackPlugin, CompressionWebpackPlugin

***Question:*** Is it possible to write your own plugin?

***Answer:*** Yes, its possible to write your own plugin and use plugins written by community.


### Development

***Question*** What is advantage of webpack-dev-derver over simple `http` server or nginx?

***Answer:***

***Question:*** On which platform webpack-dev-server is developed?

***Answer:*** webpack-dev-server is express (node.js) application.

***Question:*** What is Hot-Modules-Replacement?

***Answer:*** Hot-Modules-Replacement(HMR) is webpack feature which allows to update modules in application without page reload. HMR can be used as an advanced replacement for livereload.

***Question:*** How to enable source maps in webpack bundles?

***Answer:*** Using devtool: 'source-map' (there are various other configurations for source maps, view full list [here](https://webpack.js.org/configuration/devtool/#devtool))

***Question:*** How to automatically build and update bundles in browser after a change in source code?

***Answer:*** Using `watch: true` and `devServer: { hot: true }` options together.


### Optimization

***Question:***  Briefly describe long-term caching and how to achieve it using webpack?
 
***Answer:*** Browsers should cache static assets to save traffic and users time. But after each change or bugfix, browser have to download newer version of files. The most easy way to achieve this is changing file name. It could be buildId or unique hash in the end of file's name like
    
   ```javascript
       app.js?build=1
       app.js?build=2
   ```  
or 

   ```javascript
     app.js.2a6c1fee4b5b0d2c9285.js
     app.js.70b594fe8b07bcedaa98.js
   ```
  
 To achieve this using webpack simple configuration should be done
  
  
   ```javascript
      module.exports = {
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
      }
   ```


***Question:*** What is difference between `hash` and `chunkhash`
   
***Answer:*** [hash] will generate unique hash for each build and use it for all chunks. Replace `[hash]` with `[chunkhash]` to generate unique hashes for each chunk. This is useful when you dont want to re-download vendors (dependencies) file but you have changes in your application code and want to update it.
   
***Question:*** Describe CommonsChunkPlugin

***Answer:*** The CommonsChunkPlugin is built-in feature that creates a separate file (known as a chunk), consisting of common modules shared between multiple entry points. By separating common modules from bundles, the resulting chunked file can be loaded once initially, and stored in cache for later use. This results in pagespeed optimizations as the browser can quickly serve the shared code from cache, rather than being forced to load a larger bundle whenever a new page is visited.

***Question:*** Explain this code

 ```javascript
    new webpack.optimize.CommonsChunkPlugin({
      name: 'common',
      filename: 'common.js',
      chunks: ['home', 'dashboard']
    })
 ```
***Answer:*** This code creates separate file: `common.js` containing common modules from `home` and `dashboard` chunks.  

***Question:*** Which built-in plugin should be used for code minification?

***Answer:*** UglifyJS plugin.

***Question:*** What analyzes tools you use to inspect your webpack bundle?
    
***Answer:*** webpack-bundle-analyzer plugin, official webpack analyze tool, webpack visualizer, webpack chart
 
   
### Migration
***Question:*** Describe LoaderOptionsPlugin

***Answer:*** LoaderOptionsPlugin built especialy for migration from webpack 1 to webpack 2. Options for loaders now should be passed through this plugin's options section, e.g.
  
  webpack 1
  ```javascript
    module.exports = {
      eslint: {
        /* your eslint loader config */
      }
    }
  ```
  webpack 2
  ```javascript
    module.exports = {
      plugins: [
        new webpack.LoaderOptionsPlugin({
          options: {
            eslint: {
              /* your eslint loader config */
            }
          }
        })
      ]
    }
   ```


***Question:*** Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
  
***Answer:*** No, it’s now included by default.
  
***Question:*** What versions of webpack support es6 modules from box?

***Answer:*** webpack 2+

***Question:*** What versions of webpack support json-loader from box?

***Answer:*** webpack 2+


### Advanced questions

***Question:*** Describe webpack runtime and manifest.

***Answer:*** https://webpack.js.org/concepts/manifest/

***Question:*** Is it possible to use other (not js) language for webpack config file?

***Answer:*** Yes, webpack accepts configuration files written in multiple programming and data languages, such as typescript, coffeescript, babel and jsx. The list of supported file extensions can be found [here](https://github.com/js-cli/js-interpret).

***Question:*** Is it possible to have different configurations' files for different environments?

***Answer:*** Yes, read more [here](https://aishwaryavaishno.wordpress.com/2017/04/17/webpack-configuration-for-multiple-environments/)

***Question:*** Describe tree shaking mechanism.

***Answer:*** https://webpack.js.org/guides/tree-shaking/

***Question:*** What is difference between tree shaking and dead code elumination.

***Answer:*** https://medium.com/@Rich_Harris/tree-shaking-versus-dead-code-elimination-d3765df85c80
