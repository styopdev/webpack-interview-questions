# Webpack interview questions

[View version with answers](https://github.com/styopdev/webpack-interview-questions/blob/master/answers.md)

## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Development](#development)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced questions](#advanced-questions)
* [Internal API Questions (very advanced)](#internal-api-questions-very-advanced)

### Concepts
* What is webpack?
* What is the main difference between webpack and other build tools like gulp or grunt?
* What is bundle in webpack?
* In which environment webpack works?
* What is `entry` point?
* What is dependency graph and how webpack build it?
* Which modules design patterns webpack supports out of the box?

### Config file
* What is the format of webpack's config file.
* Is it possible to have multiple entry points in single webpack configuration file?
* Is it possible to define multiple configurations for different environments?
* How to generate webpack config file automatically?

### Loaders 
* What is loader in webpack?
* Where loaders should be defined?
* What is the difference between a rule and a loader?
* Explain this code
    ```javascript
    {
      test: /\.scss$/,
      loaders: ['style-loader', 'css-loader?sourceMap', 'sass-loader?sourceMap', 'postcss-loader'],
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

### Development
* What is advantage of webpack-dev-server over simple `http` server or nginx?
* On which platform webpack-dev-server is developed?
* What is Hot-Modules-Replacement?
* Does it make sense to use Hot-Modules-Replacement in production environment?
* How to enable source maps in webpack bundles?
* How to automatically build and update bundles in browser after a change in source code?


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
* How to achieve lazy loading in webpack?
* What analyzes tools you use for webpack bundle's inspection?


### Migration
* Describe LoaderOptionsPlugin.
* Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
* Which versions of webpack support es6 modules from box?
* Which versions of webpack support json-loader from box?
* Which versions of webpack support code splitting?


### Advanced questions
* Describe webpack runtime and manifest.
* Is it possible to use other language (except javascript) for webpack config file?
* Is it possible to have different configurations' files for different environments?
* Describe tree shaking mechanism.
* What is difference between tree shaking and dead code elumination.
* Describe scope hoisting in webpack 3.
* What is Tapable and how does it relate to webpack plugins?

### Internal API Questions (very advanced)
* What is the difference between Compiler and Watching classes?
* Describe the purpose of Compiler
* Describe the purpose of Compililation
* Describe DependenciesBlock class. Why is it so important.
* Describe the relationship between the Parser, Dependency, Dependency Factory, and Dependency Templates
