# Webpack interview questions (DRAFT VERSION)

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


### Config file
* What is the format of webpack's config file.
* Is it possible to have multiple entry points in singe webpack configuration file?
* Where loaders should be defined?


### Loaders 
* What is loader in webpack?
* Do loaders work in synchronous or asynchronous way?
* Is it possible to use multiple loaders in `rules` single object?
* Name loaders you think are very important and helpful

 
### Plugins 
* Describe plugin in webpack
* What is difference between loader and plugin?
* Name plugins you think are very important and helpful


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
* Describe CommonsChunkPlugin
* What analyzes tools you use to inspect your webpack bundle?



### Migration
* Describe LoaderOptionsPlugin
* Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
* What versions of webpack support es6 modules from box?
* What versions of webpack support json-loader from box?


### Advanced questions
* Describe webpack runtime and manifest 
* Is it possible to use other (not js) language for webpack config file?
