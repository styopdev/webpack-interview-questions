# Webpack interview questions

[View version with answers](https://github.com/styopdev/webpack-interview-questions/blob/master/answers.md)

## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Debugging](#debugging)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced-questions](#advanced-questions)

### Concepts
* What is webpack?
* What is the main difference between webpack and other build tools like gulp or grunt?
* What is bundle in webpack?
* In which environment webpack works?
* What is `entry` point?
* What is dependency graph and how webpack build it?

### Config file
* What is the format of webpack's config file.
* Is it possible to have multiple entry points in single webpack configuration file?
* Is it possible to define multiple configurations for different environments?

### Loaders 
* What is loader in webpack?
* Where loaders should be defined?
* Explain this code
    ```javascript
    {
      test: /\.scss$/,
      loaders: ['style', 'css?sourceMap', 'sass-loader?sourceMap', 'postcss-loader'],
      exclude: /node_modules/
    }
    ```
* Do loaders work in synchronous or asynchronous way?
* Is it possible to use multiple loaders in `rules` single object?
* Name loaders that you think are very important and helpful.

 
### Plugins 
* Describe plugin in webpack.
* What is difference between loader and plugin?
* What is advantage of CompressionPlugin?
* How to move some data (e.g css code) from bundle to separate file in webpack?
* Name plugins you think are very important and helpful.
* Is it possible to write your own plugin?

### Debugging

### Optimization
* Briefly describe long-term caching and how to achieve it using webpack?
* What is difference between
  
    ```javascript
       ...
       output: {
        filename: "[name].[hash].js"
       }
       ...
   ```
    and
   ```javascript
      ...
       output: {
        filename: "[name].[chunkhash].js"
       }
       ...
    ```
* Describe CommonsChunkPlugin.
* Explain this code
 ```javascript
    new webpack.optimize.CommonsChunkPlugin({
      name: 'common',
      filename: 'common.js',
      chunks: ['home', 'dashboard']
    })
  ```
* Which built-in plugin should be used for code minification?
* Explain this code
 ```javascript
    new webpack.ContextReplacementPlugin({
      /moment[\/\\]locale/,
      /(en-gb|en-us)\.js/
    })
  ```
* What analyzes tools you use for webpack bundle's inspection?


### Migration
* Describe LoaderOptionsPlugin.
* Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
* Which versions of webpack support es6 modules from box?
* Which versions of webpack support json-loader from box?


### Advanced questions
* Describe webpack runtime and manifest.
* Is it possible to use other (not js) language for webpack config file?
* Is it possible to have different configurations' files for different environments?
* Describe tree shaking mechanism.
* What is difference between tree shaking and dead code elumination.
* Describe scope hoisting in webpack 3.
