### 1. JavaScript操作数组的方法有哪些？
`array.push(): 向数组末尾添加一个元素
`array.pop(): 删除数组的最后一个元素

`array.unshift(): 向数组开始添加一个元素
`array.shift(): 删除数组的第一个元素

`array.sort(): 对数组元素进行排序，默认按字符串顺序排序
`array.reverse(): 反转数组中的元素顺序

`array.splice(): 可以在指定位置添加或删除元素，也可以用于替换元素
`array.slice(): 返回一个从指定位置开始到结束位置的子数组，原数组不变`

`indexOf() 和 lastIndexOf()：分别用于查找元素第一次出现的位置和最后一次出现的位置
`array.concat(other)：将多个数组合并成一个新数组
`array.join(): 将数组中的元素连接成一个字符串

`array.map()：遍历数组并对每个元素执行操作，返回操作后的新数组
`array.filter(): 返回满足条件的所有元素组成的新数组
`array.forEach(): 遍历数组并对每个元素执行操作，无返回值`

`array.some(): 遍历数组的每个元素，如果其中有任何一个元素满足测试函数的条件，则返回true,否则返回 false`
`array.reduce(): 从左到右累加,返回一个累积结果，可以是任何类型的值

`includes()： 检查数组是否包含指定元素，返回布尔值`
`array.isArray(): 判断一个变量是否是数组

`find() 和 findIndex()：find() 返回满足条件的第一个元素，findIndex() 返回满足条件的第一个元素的索引`
### 2. JavaScript操作字符串的方法有哪些？
	string.toLocaleLowerCase() 和 string.toLocaleUpperCase()： `将字符串转换为本地化的小写或大写形式`
	string.replace(/a/,'b'): 查找字符串所有的a,将其替换成b
	string.split(''): 将字符串拆分成数组，基于指定的分隔符
	string.trim()：去除字符串两端的空格
	string.substring(4,7)`: 从字符串中提取子串，其参数为起始索引和结束索引（不包括结束索引处的字符）。
	string.slice(1,3): 从字符串中提取子串，其参数为起始索引和结束索引（不包括结束索引处的字符）
	string.substr(2,5): 从字符串中提取子串，其参数为起始索引和子串的长度
### 3. 基本数据类型、引用数据类型有哪些，区别是什么？
	1. 基本数据类型:
		String Number Boolean Undefined Null symbol
		存放在栈内存里面,保存的是具体的实际值
	2. 引用数据类型:
		Array Object Function Date RegExp
		存放在堆内存里面,保存的是对象在堆内存中的引用地址
	区别：
	1. 基本数据类型是不可变的,引用数据类型是可变的,可以通过属性/方法修改
### 4. JavaScript对数据类的检测方式有哪些？
`typeof() 
`instanceof()`
`constructor()`
`object.prototype.toString().call()`                     
### 5. 说一下闭包，闭包有什么缺点？
*闭包是有权限访问 '其他函数作用域的局部变量' 的函数*
1. `由于在Js中，变量的作用域属于函数作用域，函数执行后作用域就会被清理，内存也随之收回。但是由于闭包是建立在一个函数内部的子函数，由于其可访问上级作用域的原因，即使上级函数执行完，作用域也不会随之销毁，这时的子函数(闭包),便拥有了访问上级作用域中变量的权限。`
特点：可以重复利用变量，不会污染全局。一直保存在内存中。
缺点：闭包较多的时候，会消耗内存导致页面性能下降，在IE浏览器中可能会导致内存泄漏。
使用场景：防抖，节流
### 6. 防抖和节流是什么？
**防抖：**`在事件触发后，在一定时间内不再触发事件，只有等待一段时间后没有新事件触发，才会执行一次函数
```
function debounce(func, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => {
      func.apply(this, args);
    }, delay);
  };
}

const debouncedFunction = debounce(() => {
  console.log('Debounced function executed.');
}, 300);
```
应用场景：
`1. 频繁和服务端交互(高频点击按钮)
`2. 搜索框的输入
`3. 窗口大小发生变化`
**节流：**`指在一段时间内只允许函数执行一次，无论事件触发多频繁。节流常用于限制用户频繁操作
```
function throttle(func, interval) {
  let lastTime = 0;
  return function(...args) {
    const currentTime = Date.now();
    if (currentTime - lastTime >= interval) {
      func.apply(this, args);
      lastTime = currentTime;
    }
  };
}

const throttledFunction = throttle(() => {
  console.log('Throttled function executed.');
}, 300);

```
应用场景：
`1. scroll事件
`2. 滚动、拖拽`
### 5. 哪些操作会导致内存泄漏？
`Js已经分配内存地址的对象,但是由于长时间没有释放或者没办法清除,造成长期占用内存的现象，会让内存资源大幅浪费，最终导致运行速度慢，甚至崩溃的情况。(不能回收)`
因素：
1. 意外的全局变量
2. 一些未清空的定时器
3. 过度的闭包
4. 一些引用元素没有被清除
### 6. 事件委托(也叫事件代理)是什么？
*利用事件冒泡的机制来实现，也就是把子元素的事件绑定到父元素的身上*，如果子元素阻止了事件冒泡，那么委托也就不成立
阻止事件冒泡：event.stopPropagation()
addEventListener('click',函数名,true/false),默认是false(事件冒泡),true(事件捕获)
优点：提高性能,减少事件的绑定，也就减少了内存的占用
### 7. 基本数据类型和引用数据类型的区别？
1. 基本数据类型：*String Number Boolean undefined null*
保存在==栈内存==中,保存的就是一个具体的值
2. 引用数据类型(复杂数据类型)：*Object Array Function*
保存在==堆内存==中,声明一个引用类型的变量,保存的是引用类型数据的地址
### 8. 说一下原型链和作用域链的区别
**原型链：**`指对象之间通过原型（prototype）属性连接起来的链式结构。每个对象都有一个原型对象，它可以是另一个对象，从而形成原型链`
流程：`当访问一个对象的属性时，如果对象本身没有该属性，JavaScript 会沿着原型链向上查找，直到找到该属性或者到达原型链的顶端(通常是Object.prototype)`
**作用域链：**`指函数的变量访问规则。每个函数都有自己的作用域，包括其自身的变量和参数，以及外部函数的变量。`
流程：`当在函数中引用一个变量时，JavaScript 会首先在当前函数的作用域中查找，然后依次向外层函数的作用域查找，直到全局作用域`
区别：
	`1. 原型链关注对象之间的继承关系，用于属性的查找和继承
	`2. 作用域链关注函数内部的变量访问规则，用于变量的查找和作用域控制
### ​9. new操作符做了什么？
1. 先创建一个对象
2. 把空对象和构造函数通过原型链进行链接
3. 把构造函数的this绑定到新的空对象身上
4. 根据构造函数返回的类型推断,如果是值类型,则返回对象,如果是引用类型,就要返回这个引用类型。
### 10. JavaScript是如何实现继承的？
1. 原型链继承
2. 借用构造函数继承
3. 组合式继承
4. Es6的class继承
### 11. JavaScript的设计原理
Js引擎 运行上下文 调用栈 事件循环 回调
### 12. JavaScript关于this指向的问题
1. 全局对象中的this指向
   指向是window
2. 全局作用域或者普通函数中的this
   指向全局window
3. 非箭头函数的情况下,this永远指向最后调用它的那个对象
4. new 关键词改变了this的指向
5. call,apply,bind 可以改变this指向,不是箭头函数
6. 箭头函数中的this
    它的指向在定义的时候就已经确定了,箭头函数它没有this,看外层是否有函数,有就是外层函数的this,没有就是window
7. 匿名函数中的this
    永远指向window,匿名函数的执行环境具有全局性,因此this指向window
### 13. setTimeout和setInterval最小执行时间
HTML5规定内容:
setTimeout最小是4ms
setInterval最小是10ms
### 14. call,appply,bind三者有什么区别
`都是改变this指向和函数的调用,call和apply的功能类似,
`第一个参数是要绑定到函数的上下文（this）,只是传参的方法不同
*call:* `传的是一个参数列表
*apply：*`传递的是一个数组
*bind：*`传参后不会立即执行,会返回一个新的函数,绑定了指定的上下文和参数。
`总结: call方法的性能要比apply好一些,所以call用的更多一点
### ​15. 如何实现一个深拷贝和浅拷贝，区别是什么
**浅拷贝：** `浅拷贝是复制对象的一层属性，而不复制嵌套对象或数组的内容。它们都能将源对象的属性浅复制到目标对象`。
`1. 拓展运算符...`
`2.Object.assign()` 
**深拷贝：**
`深拷贝是复制对象的所有嵌套属性，包括对象和数组的内容。一种深拷贝的实现方式是递归地遍历源对象的每个属性，对于对象和数组递归进行复制。`
`1. JSON.parse(JSON.stringify())`
- `会丢失原对象的一些特殊属性和方法，例如函数、正则表达式、日期对象等，因为它们在转换为 JSON 字符串时会被丢弃。
- `循环引用的对象无法通过这种方式深拷贝，会引发 TypeError。JSON 格式不支持循环引用
`2. 递归函数实现
`function deepCopy(obj) {
  `if (obj === null || typeof obj !== 'object') {
    `return obj;
  ``}
  `const target = Array.isArray(obj) ? [] : {};
  `for (const key in obj) {
    `if (obj.hasOwnProperty(key)) {
      `target[key] = deepCopy(obj[key]);
    ``}
  ``}
  `return target;
``}
`const source = { name: 'Alice', details: { age: 30 } };
`const deepCopied = deepCopy(source);`
### 16. 说一下事件循环
Js是一个单线程的脚本语言
主线程 执行栈 任务队列 宏任务 微任务
`主线程先执行同步任务，然后才去执行任务队列里的任务，如果在执行宏任务之前有微任务，那么要先执行微任务，全部执行完之后等待主线程的调用，调用完之后再去任务队列中查看是否有异步任务，这样一个循环往复的过程就是事件循环`
### 17. ajax是什么？如何实现？
`在不重新加载整个网页的前提下，与服务器交换数据并更新内容，通过XmlHttpRequest对象向服务器发送异步请求，然后从服务器拿到数据，最后通过Js操作DOM更新页面`
### 18. get和post有什么区别？
1. get参数会放在url上，安全性较差。post是放在body中
2. get请求刷新服务器或退回是没有影响的，post请求退回时会重新提交数据
3. get请求时会被缓存，post请求不会缓存
4. get请求会被保存在浏览器历史记录中，post不会
5. get请求只能进行url编码，post请求支持很多种
### 19.  promise的内部原理是什么？它的优缺点是什么？
		Promise对象，封装了一个异步操作并且还可以获取成功或失败的结果
		promise主要就是解决回调地狱的问题,回调地狱的原因是异步任务比较多，存在相互依赖的问题,然而代码的可读性差，可维护性差。
		有三种状态：pending(初始状态) fulfilled(成功状态) rejected(失败状态)
		状态改变时只有两种情况：
			pending--->fulfilled; pending-->rejected 一旦发生,状态就会凝固,不会再变。
		首先时我们无法取消promise,一旦创建他就会立即执行,不能中途取消。
		如果不设置回调，promise内部抛出的错误就无法反馈到外部
		若当前处于pending状态时,无法得知目前在那个阶段
		原理：
		     构造一个Promise实例,实例需要传递函数的参数,这个函数有两个形参,分别是函数类型
		     一个resolve,一个reject
### 20. Promise和async await有什么区别？
	1. 都是处理异步请求的方式,Promise是Es6的语法,async await 是Es7的语法
	2. async await是基于Promise实现的，都是非阻塞性的
	优缺点：
		1. promise是返回对象要用then，catch方法去处理和捕获异常，书写方式是链式,async await是try catch 进行捕获异常
		2. async await 看起来简洁，使得异步代码看起来像同步代码，只有await的代码执行完毕后才会执行后面的代码。
		3. promise.then()的方式会出现请求还没返回，就执行了后面的操作
### 21. 浏览器的储存方式有哪些？
1. cookie
2. localStorage
H5,以键值对的形式的存储,永久存储
3. sessionStorage
当前页面关闭后就会立刻清理，会话级别的存储方式
4. indexedDB
H5标准的储存方式，以键值对进行储存，可以快速读取，适合Web场景

### 22. 介绍下token
token: 验证身份的令牌，一般就是用户通过账号密码登录后，服务端把这些凭证通过加密等一系列操作得到的字符串
1. 存localStorage中，后期每次请求接口都需要把它当作一个字段传给后台
2. 存cookie中，会自动发送，缺点是不能跨域
登录流程：
1. 客户端用账号密码请求登录
2. 服务端收到请求后，需要去验证账号密码
3. 验证成功后，服务端签发一个token,把它发给客户端
4. 客户端收到token后保存起来，可以放在localStorage或者cookie
5. 客户端后续的请求，都需要携带这个token
6. 服务器收到请求，去验证客户端的token,验证成功返回数据给客户端。
### 23. 页面渲染的过程是怎样的？
1. DNS解析
2. 建立TCP请求
3. 发送HTTP请求
4. 服务器处理请求
5. 渲染页面
		浏览器会获取HTML和CSS的资源，然后把HTML解析成DOM树
		再把CSS解析成CSSDOM，把DOM和CSSDOM合并为渲染树，将渲染树的每个节点渲染(绘制)到屏幕上
### 24. JWT 认证流程
`JSON Web Token 用于在网络间传递信息的开放标准，通常用于认证和授权
**JWT的认证流程：**
`1. 前端把账号密码发送给后端的接口
`2. 服务器核对账号密码成功后，把用户id等其他信息作为JWT 负载，把它和头部分别进行base64编码拼接后签名，形成一个JWT (token)。
`3. 前端每次请求时都会把JWT放在HTTP请求头的Authorization宇段内
`4. 后端检查是否存在，如果存在就验证JWT的有效性（签名是否正确，token是否过期）
`5. 验证通过后端使用JWT中包含的用户信息进行其他的操作,并返回对应结果
`此外JWT 具有一定的时效性,可以设置过期时间,从而强制用户在一段时间后重新登录以获取新的 JWT
### 25. HTTP协议对丁的协议头和请求头有什么？
1. 请求头信息：
	Accept: 浏览器告诉服务器所支持的数据类型
	Host: 浏览器告诉服务器访问的主机
	Referer: 浏览器告诉服务器我是从哪里来的(防盗链)
	User-Agent: 浏览器类型、版本信息
	Date: 浏览器告诉服务器我是什么时候访问的
	Connection: 连接方式
	Cookie
	X-Request-With: 请求方式
2. 响应头消息
	Location: 告诉浏览器去找谁
	Server: 告诉浏览器服务器的类型
	Content-Type: 告诉浏览器返回的数据类型
	Refresh: 控制的定时刷新
### 26. 说一下浏览器的缓存策略
强缓存(本地缓存) 弱缓存(协商缓存)
强缓存：不发起请求，直接使用缓存里的内容，浏览器把Js,css,image等存到内存中，下次用户访问直接从内存中取，提高性能
协商缓存：需要像后台发请求，通过判断来决定是否使用协商缓存，如果请求内容没有变化，则返回304，浏览器就用缓存里的内容。
强缓存的触发：
	HTTP1.0：时间戳响应头
	HTTP1.1: Cache-Control响应头
协商缓存的触发：
	HTTP1.0: 请求头: if-modified-since 响应头：last-modified
	HTTP1.1: 请求头: if-none-match 响应头：Etag
### 27. 同源策略、解决跨域
http:// www.baidu.com :8080      /index/vue.js
协议    域名                   端口号 
`如果两个URL 的协议、端口和主机都相同的话，则这两个 URL 是同源的。
`其中一个不一样都会产生跨域，img，link，script允许跨域加载资源的标签。

*JSONP：* `script标签可以跨域请求资源，将回调函数作为参数拼接在url中。后端收到请求，调用该回调函数，并将数据作为参数返回去，设置响应头返回文档类型为javascript。仅支持GET

*CORS:* `后端设置 Access-Control-Allow-Origin 响应头为目标host`

*Proxy:* `通过该服务器转发请求至目标服务器，得到结果再转发给前端，但是最终发布上线时如果web应用和接口服务器不在一起仍会跨域

`vue.config.js
```
 proxy: {
    '/api': {  '/api'是代理标识，url前面是/api的就是使用代理的
        target: "http://xxx.xx.com:8080", 目标地址，一般是指后台服务器地址
        changeOrigin: true, 是否跨域
        pathRewrite: { pathRewrite 的作用是把实际Request Url中的'/api'用""代替
            '^/api': "" 
                }
            }
        }
```

`通过axios发送请求_配置请求的根路径
```
axios.defaults.baseURL = '/api'
```
