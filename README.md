# Webpack interview questions (DRAFT VERSION)


## Table of Contents

* [Concepts](#concepts)
* [Config file](#config-file)
* [Loaders](#loaders)
* [Plugins](#plugins)
* [Debugging](#debugging)
* [Optimization](#optimization)
* [Migration](#migration)
* [Advanced-questions](#advanced-questions)
* [Answers](#answers)

### Concepts
* What is webpack?
* What is the main difference between webpack and other build tools like gulp or grunt?
* What is bundle in webpack?
* In which environment webpack works?
* What is `entry` point?

[View Answers](#concepts-answers)

### Config file
* What is the format of webpack's config file.
* Is it possible to have multiple entry points in singe webpack configuration file?
* Where loaders should be defined?

[View Answers](#config-file-answers)

### Loaders 
* What is loader in webpack?
* Do loaders work in synchronous or asynchronous way?
* Is it possible to use multiple loaders in `rules` single object?
* Name loaders you think are very important and helpful

[View Answers](#loaders-answers)
 
### Plugins 
* Describe plugin in webpack
* What is difference between loader and plugin?
* Name plugins you think are very important and helpful

[View Answers](#plugins-answers)

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


[View Answers](#optimization-answers)

### Migration
* Describe LoaderOptionsPlugin
* Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
* What versions of webpack support es6 modules from box?
* What versions of webpack support json-loader from box?

[View Answers](#migration-answers)

### Advanced questions
*
*
*

## Answers

### Concepts answers
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

***Answer:***
  
***Question:*** What is dependency graph and how webpack builds it?

***Answer:***
 
  [<- Back](#concepts)

### Config file answers
***Question:*** What is the format of webpack's config file.
  
***Answer:*** webpack's config file is javascript file in commonjs module pattern.

***Question:*** Is it possible to have multiple entry points in singe webpack configuration file?
  
***Answer:*** Yes
  
***Question:*** Where loaders should be defined?

***Answer:*** in the rules property

  [<- Back](#config-file)

### Loaders answers
***Question:*** What is loader in webpack
  
***Answer:*** Loaders are transformations that are applied on the source code of a module. webpack supports modules written in a variety of languages and preprocessors, via loaders. Loaders describe to webpack how to process non-javaScript modules and include these dependencies into your bundles.
  
***Question:*** Do loaders work in synchronous or asynchronous way?
  
***Answer:*** Both. Loaders can work synchronous or asynchronous.

***Question:*** Is it possible to use multiple loaders in `rules` single object?
  
***Answer:*** Yes, its possible to chain loaders.

***Question:*** Name loaders you think are very important and helpful

***Answer:*** raw-loader, url-loader, html-loader, file-loader, style-loader, css-loader, script-loader, babel-loader, loaders for typescript, coffescript, less, sass, pug, markdown, etc.

  [<- Back](#loaders)

### Plugins answers
***Question:*** Describe plugin in webpack

***Answer:*** 

***Question:*** What is difference between loader and plugin

***Answer:*** 

***Question:*** Name plugins you think are very important and helpful

***Answer:*** CommonsChunkPlugin, DefinePlugin, HtmlWebpackPlugin, ExtractTextWebpackPlugin, CompressionWebpackPlugin
  
  [<- Back](#plugins)

### Debugging answers

  [<- Back](#debugging)
  
### Optimization answers
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

***Answer:*** 
 
***Question:*** What analyzes tools you use to inspect your webpack bundle?
    
***Answer:*** webpack-bundle-analyzer plugin, official webpack analyze tool, webpack visualizer, webpack chart
 
  [<- Back](#optimization)
   
### Migration answers
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

  [<- Back](#migration)

### Advanced questions answers

  [<- Back](#advanced-questions)
