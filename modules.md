## 模块化
- 立即执行函数 
  
  (function(){})() ：可以防止“污染”全局变量、防止变量名冲突、保护私有成员
- CommonJs规范
  
  同步加载require('module')
  
  模块定义module.exports=
- AMD规范
  
  异步加载，依赖前置require([module], callback)
  
  常用模块定义define([modeule],function(){ return {}; })
  
  目前，主要有两个Javascript库实现了AMD规范：require.js和curl.js
- CMD规范
  
  异步加载，依赖延迟require(id)
  
  常用模块定义define(function(require, exports, module) { module.exports||return });
  
  目前，实现了CMD规范：sea.js
- ES2015 import， 异步加载
