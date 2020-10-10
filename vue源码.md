强类型语言

类型检查，在编译期尽早发现bug，而不是在运行时发现，不影响代码的运行

Vue 2 引入了 Flow 做静态类型检查

通常类型检查分成 2 种方式：

- **类型推断**：通过变量的使用上下文来推断出变量类型，然后根据这些推断来检查类型。
- **类型注释**：事先注释好我们期待的类型，Flow 会基于这些注释来判断。



源码目录

```
src
├── compiler        # 编译相关 
├── core            # 核心代码 
├── platforms       # 不同平台的支持
├── server          # 服务端渲染
├── sfc             # .vue 文件解析
├── shared          # 共享代码
```



**Vue 源头**

用函数实现的一个类，类原型上挂很多方法和属性

```
import { initMixin } from './init'
import { stateMixin } from './state'
import { renderMixin } from './render'
import { eventsMixin } from './events'
import { lifecycleMixin } from './lifecycle'
import { warn } from '../util/index'

function Vue (options) {
  if (process.env.NODE_ENV !== 'production' &&
    !(this instanceof Vue)
  ) {
    warn('Vue is a constructor and should be called with the `new` keyword')
  }
  this._init(options)
}

initMixin(Vue)
stateMixin(Vue)
eventsMixin(Vue)
lifecycleMixin(Vue)
renderMixin(Vue)

export default Vue

```

问题：为何 Vue 不用 ES6 的 Class 去实现？

我们往后看这里有很多 `xxxMixin` 的函数调用，并把 `Vue` 当参数传入，它们的功能都是给 Vue 的 prototype 上扩展一些方法，Vue 按功能把这些扩展分散到多个模块中去实现，而不是在一个模块里实现所有，这种方式是用 Class 难以实现的。这么做的好处是非常方便代码的维护和管理，这种编程技巧也非常值得我们去学习。



数据驱动： 视图是由数据驱动生成的





Diff 算法

对比新旧节点

新旧节点相同走patchVnode

新旧节点不同 创造一个新的，更新父占位符节点，删掉旧的节点



