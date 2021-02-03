# diff算法思路

- 对比新旧Vnode，是相同节点吗？
  - 不是
    - 找到当前oldVnode对应的真实元素节点的父节点
    - 根据Vnode生成新元素
    - 将新元素添加进父元素
    - 移除以前的旧元素节点
    - oldVnode = null
  - 是
    - 找到对应的真实dom，称为`el`
    - 判断`Vnode`和`oldVnode`是否指向同一个对象，如果是，那么直接`return`
    - 如果他们都有文本节点并且不相等，那么将`el`的文本节点设置为`Vnode`的文本节点。
    - 如果`oldVnode`有子节点而`Vnode`没有，则删除`el`的子节点
    - 如果`oldVnode`没有子节点而`Vnode`有，则将`Vnode`的子节点真实化之后添加到`el`
    - 如果两者都有子节点，则执行`updateChildren`函数比较子节点，这一步很重要
      - 分别对`oldS、oldE、S、E`两两做`sameVnode`比较，有四种比较方式，当其中两个能匹配上那么真实dom中的相应节点会移到Vnode相应的位置

