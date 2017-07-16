# Webpack interview questions (EARLY DRAFT VERSION)


* What is webpack?
   
  A: webpack is a module bundler for javaScript applications. Webpack recursively builds every module in your application, then packages all of those modules into a small number of bundles.

* What is module in this context?
  
  A:  Module is -
 
* What is webpack bundle?
   
  A:

* In which environment webpack works?
  
  A: Describe webpack configuration files
 
 * What is loader in webpack
  
  A: Loaders are transformations that are applied on the source code of a module. webpack supports modules written in a variety of languages and preprocessors, via loaders. Loaders describe to webpack how to process non-javaScript modules and include these dependencies into your bundles. The webpack community has built loaders for a wide variety of popular languages and language processors.

* Describe plugin in webpack
  
  A: webpack plugin is -

* What is difference between loader and plugin?
  
  A:

* Name loaders you think are very important and helpful
  
   raw-loader, url-loader, html-loader, file-loader, style-loader, css-loader, script-loader, babel-loader, loaders for typescript, coffescript, less, sass, pug, markdown, etc.
   
* Name plugins you think are very important and helpful
  
  A: CommonsChunkPlugin, DefinePlugin, HtmlWebpackPlugin, ExtractTextWebpackPlugin, CompressionWebpackPlugin

* Briefly describe long-term caching and how to achieve it using webpack?</summary>
  
  A:  Browsers should cache static assets to save traffic and users time. But after each change or bugfix, browser have to download newer version of files. The most easy way to achieve this is changing file name. It could be buildId or unique hash in the end of file's name like
    
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
  module.exports = {
  
  ```javascript
    output: {
     filename: "[name].[hash].js"
    }
   ```
   
In this case webpack will generate unique hash for each build and use it for all chunks. Replace `[hash]` with `[chunkhash]` to generate unique hashes for each chunk. This is useful when you dont want to re-download vendors (dependencies) file but you have changes in your application code and want to update it.


* Describe CommonsChunkPlugin
    
    A: 

* What analyzes tools you use to inspect your webpack bundle?
    
    A:
