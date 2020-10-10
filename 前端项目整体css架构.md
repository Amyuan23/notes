# 关于前端项目整体css架构的思考

## 前言

主要应用于后台管理系统 （`vue` + `element ui`), 其它项目也可参照此进行设计。

目的： 使得单个页面几乎不用写css代码，且极易维护，遇到ui整改什么的也能hold住

## 设计思路

组合大法好，清晰易修改

## 整体架构

1. 全局css 文件设计
   1. Reset:  重置一些样式
   2. 颜色变量与颜色class： 方便修改整个项目的主题色
   3. `mixin.scss`, 写一些BEF模式所需的混合宏
   4. 布局css 类似于 flex pointer border 这些
   5. Helper css ，layout 相关的class 例如： margin padding ，动画类，常用的如文本溢出类
2. 全局布局组件设计
   1. Card  row col 这些 ，会去承载一些复杂的css 布局 
   2. 基础组件库再封装






