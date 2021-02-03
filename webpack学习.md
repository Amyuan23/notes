## webpack 介绍

前端发展的产物 模块化打包方案 工程化方案

webpack 是js应用程序打包神器。模块化打包是它的核心。gulp grunt 是帮助实现自动化的，打包只是其中一方面

为什么要打包？

逻辑多，文件多，项目的复杂度提高了。

除了打包，还能兼容低版本



loader 和 plugin



## 前端模块化

http ， render， 

不同脚本的作用域冲突

->解诀： 命名空间。 命名空间还是比较危险。

-> 避免随意的串改-> 闭包+立即执行函数->模块作用域，暴露该暴露的，隐藏该隐藏的

**模块化的目的： 作用域封装，重用性，解除耦合**

es6 module 出现， 语法级别的支持



## webpack 打包机制

### webpack 与立即执行函数的关系

![image-20201020133442323](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201020133442323.png)

### 打包的核心机制

- 从入口文件开始，分析整个应用的依赖树
- 将每个依赖模块 包装起来，放到一个数组中等待调用
- 实现模块加载的方法，并把它放在模块执行的环境中，确保模块间可以互相调用
- 把执行入口文件的逻辑放到立即执行函数中去执行



npm 包管理器

^ 号是动态版本 （中版本和小版本）



![image-20201020140309465](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201020140309465.png)

  **一切皆模块**

loader  web pack 能力的扩展



加载顺序和use 里面写的顺序是相反的



Plugin 强调事件监听， // 例如压缩代码， 节点维度
loader 是文件维度的，往往是对文件做操作



## 性能优化

- 加快构建速度，减少查找，减少解析
  - 使用缓存
  - 使用include
  - 使用多线程, happyPack (plugin)

- 压缩
  - 去掉没有用的代码
  - 去掉debugger, console 等一系列无用代码 ,无用代码消除

- Tree shaking
- 