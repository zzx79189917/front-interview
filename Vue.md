##### Vue特点
Vue最大特点我感觉就是“组件化‘和”数据驱动“？
组件化就是可以将页面和页面中可复用的元素都看做成组件，写页面的过程，就是写组件，然后页面是由这些组件”拼接“起来的组件树。
数据驱动就是让我们只关注数据层，只要数据变化，页面(即视图层)会自动更新，至于如何操作dom，完全交由Vue去完成，咱们只关注数据，数据变了，页面自动同步变化了，很方便。

##### vue的父子组件间通信
父组件通过prop给子组件下发数据，子组件通过$emit触发事件给父组件发送消息，即prop向下传递，事件向上传递。

#####生命周期
![avatar](https://cn.vuejs.org/images/lifecycle.png)

##### vue搭建
[链接](https://zhuanlan.zhihu.com/p/70752505)