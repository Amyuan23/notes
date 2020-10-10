# vue3入门尝鲜



## 体验方式

1. Vue-cli3

   ```powershell
   $ vue create vue3-cli-demo
   $ vue add vue-next // 此命令将vue2项目升级为vue3
   ```

2. vite

   ```powershell
   $ npm install -g create-vite-app
   $ create-vite-app vue3-vite-demo
   ```

   



当要去理解一个组件时，我们更加关心的是“这个组件是要干什么” (即代码背后的意图) 而不是“这个组件用到了什么选项”。基于选项的 API 撰写出来的代码自然采用了后者的表述方式，然而对前者的表述并不好。

基于选项的API 有一个很大的缺点是逻辑分离，处理同一逻辑的代码会非常分散，正是这种碎片化使得理解和维护一个复杂的组件变得非常困难。

基于逻辑关注代码



![image-20200922100710952](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200922100710952.png)

![image-20200922100735469](/Users/yuanxue/Library/Application Support/typora-user-images/image-20200922100735469.png)

