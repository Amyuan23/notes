# vue3是如何变快的

- 快1.2～2倍
- diff算法，vue2是全量对比，静态标记
- 静态提升
- 事件监听缓存

![image-20200923093957742](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200923093957742.png)

![image-20200923095239623](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200923095239623.png)

![image-20201012140706599](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201012140706599.png)

在beforecreate之前完成的，没有this

![image-20201012142314505](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201012142314505.png)

![image-20201012185003032](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201012185003032.png)

![image-20201013154747549](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201013154747549.png)

![image-20201013161604336](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201013161604336.png)

![image-20201013170952056](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201013170952056.png)

![image-20201013173547147](/Users/yuanxue/Library/Application Support/typora-user-images/image-20201013173547147.png)

