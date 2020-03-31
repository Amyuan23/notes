# 使用element-ui遇到的问题总结



## el-table 在flex下的宽度自适应问题

解决方案：可以将设置了flex属性的容器设置`position:relative`，然后在el-table外加一层div，设置该`position:absolute; width:100%;`继承父级宽度