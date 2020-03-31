# 背景图

由于只支持线上图片和base64图片，不支持本地图片

所以，需要把图片转成base64格式的文本

[工具网站]: https://c.runoob.com/front-end/59



# 变量-主题颜色设定

wxss的变量用法和css一致

在 `static/css`路径下建`theme.wxss`

里面代码:

```css
page{
    --primary-color: #fb4d3e;
}
```

在`app.wxss`里：

```css
@import 'static/css/theme.wxss';
```

在`index.wxss`里使用:

```css
view{
    color: var(--primary-color);
}
```



# 