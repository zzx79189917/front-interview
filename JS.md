##### 对闭包的理解，以及哪些地方用过闭包，以及闭包的缺点
闭包就是能够读取其他函数内部变量的函数
缺点：由于闭包携带包含它函数的作用域，因此比其他函数占用的内存更多，泄露内存；
优点：减少创建全局变量 减少传递给函数的参数量
它的最大用处有两个，一个是可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中，不会在外部函数调用后被自动清除。

##### 什么是跨域？
跨域是指一个域下的文档或脚本试图去请求另一个域下的资源，这里跨域是广义的。
跨域并不是请求发不出去，请求能发出去，服务端能收到请求并正常返回结果，只是结果被浏览器拦截了。之所以会跨域，是因为受到了同源策略的限制，同源策略要求源相同才能正常进行通信，即协议、域名、端口号都完全一致。

##### 什么是同源策略？
同源策略/SOP（Same origin policy）是一种约定，由Netscape公司1995年引入浏览器，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，浏览器很容易受到XSS、CSFR等攻击。所谓同源是指"协议+域名+端口"三者相同，即便两个不同的域名指向同一个ip地址，也非同源。

同源策略限制以下几种行为：
1. Cookie、LocalStorage 和 IndexDB 无法读取
2. DOM 和 Js对象无法获得
3. AJAX 请求不能发送

##### 跨域解决方案
1. 通过jsonp跨域
2. document.domain + iframe跨域
3. location.hash + iframe
4. window.name + iframe跨域
5. postMessage跨域
6. 跨域资源共享（CORS）
7. nginx代理跨域
8. nodejs中间件代理跨域
9. WebSocket协议跨域

##### JSONP的优缺点
优点
1. 它不像XMLHttpRequest对象实现的Ajax请求那样受到同源策略的限制，JSONP可以跨越同源策略；
2. 它的兼容性更好，在更加古老的浏览器中都可以运行，不需要XMLHttpRequest或ActiveX的支持
3. 在请求完毕后可以通过调用callback的方式回传结果。将回调方法的权限给了调用方。这个就相当于将controller层和view层终于分开了。我提供的jsonp服务只提供纯服务的数据，至于提供服务以 后的页面渲染和后续view操作都由调用者来自己定义就好了。如果有两个页面需要渲染同一份数据，你们只需要有不同的渲染逻辑就可以了，逻辑都可以使用同 一个jsonp服务。

缺点
1. 它只支持GET请求而不支持POST等其它类型的HTTP请求
2. 它只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行JavaScript调用的问题。
3. jsonp在调用失败的时候不会返回各种HTTP状态码。
4. 缺点是安全性。万一假如提供jsonp的服务存在页面注入漏洞，即它返回的javascript的内容被人控制的。那么结果是什么？所有调用这个 jsonp的网站都会存在漏洞。于是无法把危险控制在一个域名下.所以在使用jsonp的时候必须要保证使用的jsonp服务必须是安全可信的。

#### js的数据类型：
string array number null undefined boolean object
基本数据类型：string number null undefined boolean
引用类型：array object

##### ES6新增了什么？
1. 定义变量使用let const
2. 字符串和变量的拼接 
3. 解构变量 [a,b] =[b,a]
4. 函数的扩展,可以给函数添加默认值
5. 数组的扩展indexOf forEach map 
6. class
7. promise（具体）

##### cookie的限制条件
cookie 限制条件：cookie 的属性和 cookie 的总大小。
原始规范中限定每个域名下不超过20个cookie，早期的浏览器都遵循该规范，并且在IE7中有更近一步的提升。在微软的一次更新中，他们在 IE7 中增加 cookie 的限制数量到 50 个，与此同时 Opera 限定 cookie 数量为 30 个，Safari 和 Chrome 对与每个域名下的 cookie 个数没有限制。
发向服务器的所有 cookie 的最大数量（空间）仍旧维持原始规范中所指出的：4KB。所有超出该限制的 cookie 都会被截掉并且不会发送至服务器。

##### js数组有哪些方法
1. Array.map() 此方法是将数组中的每个元素调用一个提供的函数，结果作为一个新的数组返回，并没有改变原来的数组
```
    let newArr = arr.map(x => x*2)
```
2. Array.forEach() 此方法是将数组中的每个元素执行传进提供的函数，没有返回值，直接改变原数组
```
    num.forEach(x => x*2)
```
3. Array.filter() 此方法是将所有元素进行判断，将满足条件的元素作为一个新的数组返回
```
    let newArr = arr.filter(value >1)
```
4. Array.every() 此方法是将所有元素进行判断返回一个布尔值，如果所有元素都满足判断条件，则返回true，否则为false
```
    let arr = [1, 2, 3, 4, 5]
    arr.every(value < 4)
    arr.every(isLessThan6 >6)
```
5. Array.some() 此方法是将所有元素进行判断返回一个布尔值，如果存在元素都满足判断条件，则返回true，若所有元素都不满足判断条件，则返回false
```
    let arr= [1, 2, 3, 4, 5]
    arr.some(value < 4 ) //true
    arr.some(value > 6 ) //false
```
6. Array.reduce() 此方法是所有元素调用返回函数，返回值为最后结果,传入的值必须是函数类型
```
    let arr = [1, 2, 3, 4, 5]
    let sum = arr.reduce((a, b) => a + b)
    //sum = 15  相当于累加的效果
    与之相对应的还有一个 Array.reduceRight() 方法，区别是这个是从右向左操作的
```
7. Array.push() 此方法是在数组的后面添加新加元素，此方法改变了数组的长度
8. Array.pop() 此方法在数组后面删除最后一个元素，并返回数组，此方法改变了数组的长度
9. Array.shift() 此方法在数组后面删除第一个元素，并返回数组，此方法改变了数组的长度
10. Array.unshift() 此方法是将一个或多个元素添加到数组的开头，并返回新数组的长度
11. Array.isArray() 判断一个对象是不是数组，返回的是布尔值
12. Array.concat() 此方法是一个可以将多个数组拼接成一个数组
13. Array.toString() 此方法将数组转化为字符串
14. Array.join() 此方法也是将数组转化为字符串
15. Array.splice (开始位置， 删除的个数，元素) 万能方法，可以实现增删改

##### 数组去重的方法
1. 利用ES6的Set结合Array.from去重
```
    var arr = [5,6,8,8,6,8,6];
    var set = new Set(arr);  //Set()它类似于数组(伪数组)，但是成员的值都是唯一的，没有重复的值。
    console.log(Array.from(set)) //Array.from()将一个类数组对象或者可遍历对象转换成一个真正的数组。
```
2. 利用ES5中的IndexOf()方法
```
    function noRepeat(arr){
        var newArr = [];
        for(var i in arr){
            if(newArr.indexOf(arr[i]) == -1){ //arr中的值在newArr中不存在就返回 -1
                newArr.push(arr[i]);
            }
        }
        return newArr;
    }
```
3. 利用数组中filter方法
```
    var arr = [5,6,8,8,6,8,6];
    var newArr = arr.filter((items,index,arry)=>{ //按照某个条件过滤，返回满足条件的新数组
        return arry.indexOf(items) === index //过滤掉下标相同的值
    })
```
4. 利用对象的特性（唯一性），不能出现相同的key值
```
    function reRepeat(arr){
        var obj={};
        var newArr=[];
        for(var i = 0;i < arr.length;i ++){
            if(!obj[arr[i]]){
                obj[arr[i]]=1;
                newArr.push(arr[i]);
            }
        }
        return newArr;
    }
```
5. 排序后利用相邻的元素进行判断然后push

##### 深拷贝、浅拷贝、循环引用
[链接](https://www.jb51.net/article/140928.htm)

##### 原型链的继承
[链接](https://www.jb51.net/article/146219.htm)

##### 原型链 __proto__ prototype区别
![avatar](https://img-blog.csdn.net/20180823183227903?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xpdXhpYW83MjM4NDY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 箭头函数和普通函数的区别
1. 箭头函数是匿名函数，不能作为构造函数，不能使用new
2. 箭头函数不能绑定arguments，取而代之用rest参数...解决
```
    function A(a){
        console.log(arguments);
    }
    A(1,2,3,4,5,8);
    // [1, 2, 3, 4, 5, 8, callee: ƒ, Symbol(Symbol.iterator): ƒ]
    let C = (...c) => {
        console.log(c);
    }
    C(3,82,32,11323);
    // [3, 82, 32, 11323]
```
3. 箭头函数没有原型属性
```
var a = ()=>{
  return 1;
}

function b(){
  return 2;
}

console.log(a.prototype);  // undefined
console.log(b.prototype);   // {constructor: ƒ}
```
4. 箭头函数的this永远指向其上下文的this，没有办改变其指向;普通函数的this指向调用它的对象。
5. 箭头函数不绑定this，会捕获其所在的上下文的this值，作为自己的this值
```
var obj = {
  a: 10,
  b: () => {
    console.log(this.a); // undefined
    console.log(this); // Window {postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, frames: Window, …}
  },
  c: function() {
    console.log(this.a); // 10
    console.log(this); // {a: 10, b: ƒ, c: ƒ}
  }
}
obj.b(); 
obj.c();
```

##### CommonJS模块的特点
- 所有代码都运行在模块作用域，不会污染全局作用域。
- 模块可以多次加载，但是只会在第一次加载时运行一次，然后运行结果就被缓存了，以后再加载，就直接读取缓存结果。要想让模块再次运行，必须清除缓存。
- 模块加载的顺序，按照其在代码中出现的顺序。

##### AMD规范与CommonJS规范的兼容性
CommonJS规范加载模块是同步的，也就是说，只有加载完成，才能执行后面的操作。AMD规范则是非同步加载模块，允许指定回调函数。由于Node.js主要用于服务器编程，模块文件一般都已经存在于本地硬盘，所以加载起来比较快，不用考虑非同步加载的方式，所以CommonJS规范比较适用。但是，如果是浏览器环境，要从服务器端加载模块，这时就必须采用非同步模式，因此浏览器端一般采用AMD规范。

##### 函数防抖
```
function debounce(func, wait) {
    let timeout;  // 定时器变量
    return function() {
        clearTimeout(timeout);  // 每次触发时先清除上一次的定时器,然后重新计时
        timeout = setTimeout(func, wait);  // 指定 xx ms 后触发真正想进行的操作 handler
    };
}
//事件处理程序
function realFunc(){
    console.log("Success");
}

const input = document.getElementById('input');
input.addEventListener('keydown',debounce(realFunc,500));
```

##### 函数节流
```
function throttle(func,interval){
    let timeout;
    let startTime = new Date();
    return function (){
        clearTimeout(timeout);
        let curTime = new Date();
        if(curTime - startTime <= interval){
            //小于规定时间间隔时，用setTimeout在指定时间后再执行
            timeout = setTimeout(()=>{
                func();
            },interval)
        } else {
            //重新计时并执行函数
            startTime = curTime;
            func()
        }
    }
}
//事件处理程序
function realFunc(){
    console.log('success')
}
window.addEventListener('scroll',throttle(realFunc,100));
```

##### 路由的实现方式
hash 是 URL 中 hash (#) 及后面的那部分，常用作锚点在页面内进行导航，改变 URL 中的 hash 部分不会引起页面刷新，通过 hashchange 事件监听 URL 的变化。
改变 URL 的方式只有这几种：
- 通过浏览器前进后退改变URL
- 通过a标签改变URL
- 通过window.location改变URL

history 提供了 pushState 和 replaceState 两个方法，这两个方法改变 URL 的 path 部分不会引起页面刷新。
history 提供类似 hashchange 事件的 popstate 事件，但 popstate 事件有些不同：
- 通过浏览器前进后退改变URL时会触发popstate事件
- 通过pushState/replaceState或a标签改变URL不会触发 popstate 事件

##### 用meta实现不从缓存中获取资源
meta是用来在HTML文档中模拟HTTP协议的响应头报文。meta 标签用于网页的\<head>与\</head>中，meta 标签的用处很多。meta 的属性有两种：name和http-equiv。name属性主要用于描述网页.
```
<meta http-equiv="pragma" content="no-cache">
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content=""> 
```

##### 前端事件模型和事件委托
[链接](https://www.cnblogs.com/leftJS/p/10948138.html)

##### 函数柯里化
[链接](https://www.jianshu.com/p/2975c25e4d71)

##### 存储方式
- sessionStroage 用于临时保持同一窗口的数据，窗口关闭数据也将删除
- cookie 用于存储web页面的用户信息，当用户访问web页面时，他的名字可以记录在cookie中，在用户下一次访问该页面时，可以在cookier中读取用户访问记录,cookie中每条cookie的存储空间为4k。
- localStorage 本地存储，同时不受时间限制的数据存储，localStorage中一般浏览器支持的是5M大小

##### 判断数组的方法
[链接](https://segmentfault.com/a/1190000017790888)
- instanceof 操作符判断 
```
arr instanceof Array
```
- 对象构造函数的 constructor判断 
```
arr.constructor === Array
```
- Array 原型链上的 isPrototypeOf
```
Array.prototype.isPrototypeOf(arr)
```
- Object.getPrototypeOf 
```
Object.getPrototypeOf(arr) === Array.prototype 
```
- Object.prototype.toString
```
Object.prototype.toString.call(arr) === '[object Array]'
```
- Array.isArray

##### instance实现原理
[链接](https://blog.csdn.net/qq_38722097/article/details/80717240)

##### attribute 和 property 的区别
[链接](https://blog.csdn.net/zhy13087344578/article/details/79036967)
- property和attributies都是properties的子集，而每个attribute是attributies的子集；
- attribute可以理解为特性，可以自定义，直接在html标签上添加的和使用setAttribute添加的情况一致，即html标签添加的都是attribute属性， property则是使用xx.属性进行更改，通常来讲，更改互相影响（value除外） 
- 当添加新的非默认属性时，是不互通的 
- 一些特殊属性，则需要特殊对待

##### apply，call，bind 的区别

##### 手写bind