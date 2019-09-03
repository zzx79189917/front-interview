##### Flex布局
[链接](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool)


##### position 属性有哪些值，分别什么含义
[链接]（https://www.runoob.com/w3cnote/css-position-static-relative-absolute-fixed.html）
1. static：静态定位，默认，相当于没设置，top、right、bottom、left属性（以下简称TRBL）和z-index属性不生效。
2. fixed：固定定位，相对于浏览器窗口来定位，TRBL属性和z-index属性有效。
3. relative：相对定位，相对于直接父级来定位，TRBL属性和z-index属性有效。在文档流里。
4. absolute：绝对定位，相对于同类父级来定位，即向上查找紧邻的父级position属性为fixed/relative/absolute的元素来定位，TRBL属性和z-index属性有效。脱离文档流。
5. inherit 规定应该从父元素继承 position 属性的值。