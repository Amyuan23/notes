1. 未初始化的变量值为`null`

2. 只有布尔值`true`被视为true

3. ```dart
   bool c = a[0]?.contains(b)??false
   // 运算符？.在左边为null时阻断右边的调用
   // ？？左侧为null时，右边设为默认值
   ```

4. 异步`Future`，有点像`Promise`

5. 声明式UI -> 改变ui不是在原图改变，而是重建

6. ![image-20200401160616585](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200401160616585.png)

![image-20200401161558751](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200401161558751.png)

7. 静态资源![image-20200512180637999](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200512180637999.png)

8 无状态有状态

9.路由

Route 和 [Navigator](https://coding.imooc.com/class/321.html)

Route是应用程序的“屏幕”或“页面”的抽象（可以认为是Activity）， [Navigator](https://coding.imooc.com/class/321.html)是管理Route的Widget。[Navigator](https://coding.imooc.com/class/321.html)可以通过[push](https://coding.imooc.com/class/321.html)和[pop](https://coding.imooc.com/class/321.html) route以实现页面切换。

10.单独线程 Isolate

11.网络请求。http

```
import 'package:http/http.dart' as http;
```

12.手势

onPressed

GestureDetector->onTap