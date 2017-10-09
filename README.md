# Webpack interview questions

[View version with answers](https://github.com/styopdev/webpack-interview-questions/blob/master/answers.md)

Big thanks to [TheLarkInn](https://github.com/TheLarkInn), [raybooysen](https://github.com/raybooysen) and [johannesMatevosyan](https://github.com/johannesMatevosyan) for contribution.

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
* What is a bundle in webpack?
* In which environment does webpack work?
* What is an `entry` point?
* What is a dependency graph and how does webpack build it?
* Which modules design patterns webpack supports out of the box?

### Config file
* What is the format of webpack's config file?
* Is it possible to have multiple entry points in a single webpack configuration file?
* Is it possible to define multiple configurations for different environments?
* How can we generate webpack config file automatically?

### Loaders 
* What is a loader in webpack?
* Where should loaders be defined?
* What is the difference between a rule and a loader?
* Explain this code
    ```javascript
    {
      test: /\.scss$/,
      loaders: ['style-loader', 'css-loader?sourceMap', 'sass-loader?sourceMap', 'postcss-loader'],
      exclude: /node_modules/
    }
    ```
* Do loaders work in a synchronous or an asynchronous way?
* Is it possible to use multiple loaders in the `rules` single object?
* Name loaders that you think are very important and helpful.

 
### Plugins 
* Describe a plugin in webpack.
* What is the difference between a loader and a plugin?
* What is the advantage of CompressionPlugin?
* How can you move some data (e.g css code) from a bundle to a separate file in webpack?
* Name some plugins you think are important and helpful.
* Is it possible to write your own plugin?

### Development
* What are some advantages of using webpack-dev-server over simple `http` server or nginx?
* On which platform is webpack-dev-server developed?
* What is Hot-Modules-Replacement?
* Does it make sense to use Hot-Modules-Replacement in production environment?
* How to enable source maps in webpack bundles?
* How to automatically build and update bundles in the browser after a change in source code?
* What is `parallel-webpack` and how does it affect webpack's build process?


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
* Describe the CommonsChunkPlugin.
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
* Why is OccurenceOrderPlugin part of webpack optimization? What it has to do with module ids and topological sorting?
* What analysis tools do you use for webpack bundle's inspection?


### Migration
* Describe the LoaderOptionsPlugin.
* Do you need to include OccurenceOrderPlugin in the plugins section when use webpack 2/3?
* Which version(s) of webpack support es6 modules out the box?
* Which version(s) of webpack support json-loader out the box?
* Which version(s) of webpack support code splitting?


### Advanced questions
* Describe the webpack runtime and manifest.
* Is it possible to use other languages (except javascript) for the webpack config file?
* Is it possible to have different configuration files for different environments?
* Describe the tree shaking mechanism.
* What is the difference between tree shaking and dead code elimination.
* Describe scope hoisting in webpack 3.
* What is Tapable and how does it relate to webpack plugins?

### Internal API Questions (very advanced)
* What is the difference between Compiler and Watching classes?
* Describe the purpose of Compiler
* Describe the purpose of Compililation
* Describe DependenciesBlock class. Why is it so important?
* Describe the relationship between the Parser, Dependency, Dependency Factory, and Dependency Templates
