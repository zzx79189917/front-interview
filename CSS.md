##### Flex布局
[链接](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool)
 flex 是 flex-grow、flex-shrink、flex-basis的缩写
 默认值为 0 1 auto

##### position 属性有哪些值，分别什么含义
[链接](https://blog.csdn.net/weixin_42067967/article/details/80152403)
[链接](https://www.runoob.com/w3cnote/css-position-static-relative-absolute-fixed.html)
1. static：静态定位，默认，相当于没设置，top、right、bottom、left属性（以下简称TRBL）和z-index属性不生效。
2. fixed：固定定位，相对于浏览器窗口来定位，TRBL属性和z-index属性有效。
3. relative：相对定位，相对于直接父级来定位，TRBL属性和z-index属性有效。在文档流里。
4. absolute：绝对定位，相对于同类父级来定位，即向上查找紧邻的父级position属性为fixed/relative/absolute的元素来定位，TRBL属性和z-index属性有效。脱离文档流。
5. inherit 规定应该从父元素继承 position 属性的值。

##### 伪类与伪元素的特性及其区别：
- 伪类本质上是为了弥补常规CSS选择器的不足，以便获取到更多信息；
- 伪元素本质上是创建了一个有内容的虚拟容器；
- CSS3中伪类和伪元素的语法不同；
- 可以同时使用多个伪类，而只能同时使用一个伪元素；

##### CSS布局方式 float table flex

##### CSS水平垂直居中

##### BFC
[链接](https://blog.csdn.net/dff1993/article/details/80394150)

##### 高度塌陷
在文档流中，父元素的高度默认是被子元素撑开的，也就是子元素多高，父元素就多高。但是当为子元素设置浮动以后，子元素会完全脱离文档流，此时将会导致子元素无法撑起父元素的高度，导致父元素的高度塌陷。由于父元素的高度塌陷了，则父元素下的所有元素都会向上移动，这样将会导致页面布局混乱。
```
.clearfix:after{
    /*添加一个内容*/
    content: "";
    /*转换为一个块元素*/
    display: block;
    /*清除两侧的浮动*/
    clear: both;
}
```

##### this指向
[链接](http://caibaojian.com/deep-in-javascript-this.html)

