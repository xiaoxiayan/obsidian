1. 复用组件 相关的心得 遇到的问题
   注意组件的兼容性， 可扩展性。易读性。 尽量不写死

2. 封装通用组件和业务组件之间的区别(应该是组件封装的粒度)
   通用组件一般是 基础组件，里面实现的都是一些基础通用功能，比如像 element 中的 button， 提供了通用样式， 自定义绑定功能， 业务组件往往是代有业务属性，业务逻辑的。里面会有一些定制化的东西， 例如 业务对应的接口调用，偏向业务方的一些 样式之类。

3. css bfc 概念 触发方式 有什么作用
   bfc 是指 子元素全部浮动之后脱离文档流，父元素没有设置高度，导致高度坍塌浮动。 解决方法 clear: both , 设置父级高度。 或者设置一个 box 在对底部。 高度坍塌会造成 margin 重叠。

4. 垂直水平居中
   常用 flex 布局。 justify-content: center, align-content: center, || display: inline-block; text: center, || position: absolute, margin: 0 auto

5. css 预处理
   less, sass 等预言会有对应的 babel,

6. event loop
   事件循环。 再 js 代码 运行中， 会生成一个 运行栈，当遇到异步的时候 会 生成一个异步队列。 如 promise , nextTixt , proxy（ 微任务）, setTimeout , setInterval, script 标签 （宏任务）， 微任务的优先级高于宏任务， 当 宏任务中出现微任务时， 会再次生成一个微任务队列。 运行完微任务队列才会运行宏任务。

7. 防抖 节流
   防抖： 为了避免多次调用函数 请求的时候 ， 请求回来的数据 一直更新 ，导致页面被重复渲染，出现抖动。 防抖实现核心就是， 每次触发函数，取消上一个函数的实行。用 setTimeout, 和 clearTimeout 取消上一个操作。
   节流： 在短时间内 触发多次。 只会执行一次。 设置一个 事件 flag, 当 setTime < checktime , 就不触发。

8. es6 拼接数组
   concat , [...] 都会返回新的数组。
   都会影响原数组嘛？

9. 拓展运算符 深拷贝 还是浅拷贝
   看数据类型， 如果是基础数据类型， 就是深拷贝， 如果是 引用数据类型就是浅拷贝。
   基础数据类型： num , string , boolean, null, underfined, symbol (唯一实例。具有 id 的性质) let s1 = symBol('1') let s2 = symBol('1') s1 === s2 // false
   引用数据类型： arr, object

10. csrf xss
    csrf: 跨域伪造请求。 防范， 注意使用 csrf token, sameSite cookie
    xss: 脚本注入攻击。 转义 < >

11. promise 一定要会原理，
    简单讲讲实现原理。 本质上是通过 setTimeout 去控制的， 有三个状态（panding, rej , res ），两个队列(resQueue, rejQueue)， 默认进来时 padding , 然后判断进来的函数 ， 当调用 res 的时候，resQueue 储存
    fn resolve : 判断状态， 如果状态还在等待，进入函数，修改状态值， 调取 queue 的 内容
    fn reject 同理
    fn then 判断状态， 如果状态还在等待。 说明 resolve 还没调用， 把 fn 储存到 resque 中，
    fn catch 同理

12. promise.all
    循环运行 list 中的内容， 判断三个 函数的状态。 如果都 ok 走 then
13.

14. this，剪头函数指向，改变指向
    this 指向调用他的函数，apply, bind ,
    apply： 参数是一个数组
    call: 参数是一个一个传入， 可以传入多次
    bind: 参数是一个一个传入， 一次性传入

15. routerv2, routerv3
    routerV2 钩子函数： 常用 beforeEach， afterEach ， 全局钩子。 页面：beforeEnter， 组件内部： beforeRouteEnter， beforeRouteUpdate, beforeRouteLeave
    routerV3 钩子： 全局 router.beforeEach，afterEach， 页面 beforeEnter ， 组件 onBeforeRouteEnter, onBeforeRouteUpdate, onBeforeRouteLeave
16. vuex api
    action, mu

17. 兄弟组件传递，发布订阅模式，privod inject

vuex , 隔代传值： v-bind="$attrs" v-on="$listeners"

18. 数据为什么没更新 $set
    vue2 数据更新问题， 理论上是因为 object.defineProperty ，在定义数组的时候 实际是定义一个普通的对象属性， 而不是长度属性， 所以在 push, pop 长度变化的时候是没有监控到的， 但是尤大重写了这几个 函数 （push ,pop ,shift, unshift, splice, sort, reverse ）

19. computed

核心： flag 开关。 当触发响应式修改的时候，
vue3 : 依赖收集

20. key 的作用
    diff 算法中是通过 key 去进行优化对比的。

21. 居中布局详细。flex 所有的 api。问了个遍。 [解析](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

水平垂直居中 [解析](https://segmentfault.com/a/1190000014116655)

12. css 盒模型。

13. less，scss 的应用。变量-各种操作-嵌套-继承
    less : @p-color: #3444aa
    scss: $p-color: #3444aa

14. vue 的整个渲染流程。优势
    happy Path , 1、 create(app).mount('#root')， 返回一个 appDom 挂在根节点上 ， 流程： 初始化 -> 渲染 render -> 调用 patch 函数解析。 create(app), 创建 vnode 节点。 createVnode(type, props, children) -> render -> patch -> 判断节点类型，如果是 componet 走 renderComponet , 如果是常规 div , 走 render, .
    响应式对象的更新， proxy ， refelct, get,set 方法， 当触发 set 的时候， trigger 触发, 从 targetMap 中取出 target, 然后再从 depsMap 中， 用 key 取出对应 deps, 然后循环 deps， 获取 deps 中存储的 effect 函数，执行 effect 函数， 在收集响应式的时候就 ，已经吧 instance.update 函数，也就是 render 的函数给存储到 这个 deps，effect.run || effect.scheduler, 触发 render，
    然后 具体的更新部分， 就使用 diff 算法去计算，根据需要更新的内容更新，

15. diff 算法。3 个情况。没说清楚，疏忽了，要复习。
    1、 新的比老的长， 需要新增， 调用 patch（null, n2）
    2、 新的比老的短， 需要删除， hostRemove
    3、 乱序， 用最长递增子序列去计算，获取一个核心的 map， 然后先对比， 删除掉多余的， 然后再新增没有的

16. vue 的指令。套路。v-html、v-text。扩展 xss 攻击 。伪造服务攻击。怎么防御。
    1、 xss 攻击是 注入脚本攻击， 做好转义
    2、伪造服务攻击 要做好 scrf token, 让请求都带上 tonken, 还有设置 httpOnly 的 cookie

17. 浏览器的输入到页面显示
    1、url 回车，dns 解析正确的 ip 地址， 然后请求 ip，tcp 三次握手，发送 http 请求获, 服务器处理请求并且返回响应， 浏览器渲染页面，解析 html， 构建 domtree, 解析 css, 构建 cssom, 结合 domtree 和 cssomTree, 解析 js， 布局绘制。
    处理后续资源加载， 如图片。
    扩展 回流 ， 重绘
    回流是指 ，能改变页面元素的， 比如改变元素的 大小。 字体的颜色， 元素的布局。 之类的都会 回流
    重绘只是重新绘制， 如改变 颜色 之类的，。

18. 扩展 dns 的整个流程
    1、用户输入 url 回车
    2、浏览器会检查自己的 DNS 缓存
    3、如果浏览器缓存， 查询 操作系统缓存， 如 windows ， ipconfig/displaydns
    4、如果操作系统也没有， 查询本地 dns 服务器， 就是 路由其或者网络设置中，
    5、 DNS 递归查询过程， 本地 DNF 向根服务器发送请求， 如 。com, .org , .net， 顶级域名服务器 , 权威域名服务器， example.com
    6、返回查询结果， 本地 DNS 服务器会储存起来
    7、操作系统返回结果给浏览器

优化， 使用 dns 缓存
2、 使用高性能公共 DNS 服务器， 如 goole dns 8.8.8.8
3、 浏览器使用 dns 预解析， <link rel = 'dns-prefetch'  href="//example.com">
4、启用 cdn 内容分发网络
5、使用 HTTP/2 或 HTTP/3 19. 拓展 。页面是怎么渲染的。dom-css 结合。
cssom 和 htmldom 会结合成 renderTree

20. webpack 的优化，插件使用。vite 的原理。
    vite: 1、原生 esm 支持， 支持 import export 的语法， 从 http 服务器按需加载模块
    2、按需加载， 只有子啊实际使用时候才会加载
    3、模块热替换（HMR）， 通过监听文件变化，快速响应推送更新到浏览器。
    生产环境打包：
    rollup 打包工具， 优势是 rollup 的 tree shaking 和静态分析能力更强， 能更好的移除未使用的代码
    自动代码拆分，
    css 和其他资源的优化，esbuild 构建

21. 一道算法。

22. 防抖节流。需要复习。写一个函数，输入这个函数。return 一个自带节流的函数出来。

function fangdou （fnc, delay） {
let timeout
let timeoutId = 0
return function (...arg) {
const now = new Date.now()
if (now - lastCall < delay) {
if (timeoutId ) clearTimeout(timeoutId )

         timeoutId = setTimeout(() => {
            // 记录触发的时间
            lastCall = Date.now()
            fnc.apply(this, ...arg)
         }, delay)
      } else {
         lastCall = now
         fnc.apply(this , args)
      }

}
}

23. 父子组件传值，发布订阅，provied inject？ $attr，$listen

24. 继承。底层。除了 extend 还要啥（https://segmentfault.com/a/1190000016708006）
    原型链继承， 寄生组合结成
25. 比如给一个 a 。给一个 b 去继承 a
    function createObject (extendFn) {
    function Fn () {}
    Fn.protoType = extendFn
    return new Fn()
    }

function duixect(duix) {
var newObj = {}
Object.setPrototypeOf(newObj ,duix)
return newObj
}
注意要创造一个新的对象去继承， 再函数里面， 不然会污染

26. 原型链

27. eventloop 宏任务微任务概念

28. css3 新增的方法。es6。7 新增
    es6 :
    1、箭头函数，
    2、块级作用域
    3、模板字符串
    4、const {} = data 赋值结构
    5、默认参数 function (a = '1')
    6、 展开运算符 ...
    7、模块化 ，导入导出 export, import
    8、类
    9、promise

29. 运算符可以使用哪些类型。他是怎么去实现的
    JavaScript 运算符的实现机制
    JavaScript 的运算符大多数是在引擎的 内部算法 中通过多种类型的 隐式转换 和 抽象操作 来实现的。以下是常用的内部算法：

ToPrimitive：将对象转换为原始值。
ToNumber：将非数字转换为数字。
ToBoolean：将值转换为布尔值（如 0, null, undefined, NaN, '' 为 false）。
ToString：将值转换为字符串。

30. 前端优化。除了代码方面。webpack。还有哪些。想套路答案没套路出来
    1、资源加载优化： 图片优化， 压缩图片。 懒加载。使用 cdn 资源， 还有资源缓存， 要么 就是 service worker , 离线缓存
    2、网络优化， 减少请求次数， 资源合并， 成一个文件、、 一部加载， <script src="script.js" async></script> <!-- 异步加载 -->
    <script src="script.js" defer></script> <!-- 延迟加载 -->

    按需加载： 动态加载 JavaScript 模块或第三方库（例如，React、Vue 路由懒加载），只有在需要时加载相关资源。
    DNS 预解析与预连接
    <link rel="dns-prefetch" href="https://example.com">
    <link rel="preconnect" href="https://example.com">
    3、 渲染优化
    3.1 资源加载顺序

31. 实现一个三行的文字。最后超出的…
    clamp="3"

32. 项目中做了啥最有成就感，我说了虚拟列表，没讲清楚，需要复习

33. 项目的流程。

34. elment 组件的具体使用，和属性，考验你是不是真的会用。问了一个没用过的框架，顺手搞搞你心态

35. v2 对比 v3

36. new 的实现原理，做了什么
    Object.create, 创建一个对象， 并且绑定传进来的 原型链
37. 0.1 + 0.2

38. vue-router params 和 query 区别（query 放到 ul 里面）
    query 会放到 url 上， 刷新还会保留
39. webpack loader 和 plugins
    Loaders 的作用转换， 把文件格式编译转换， 如 ts, scss
    Plugins 插件，主要是注重于打包优化、资源管理和环境变量注入等更广泛的任务。
40. less，sass 的全局变量应用
    @import 映入
41. v2 Object.definedPrototy 为什么不能监听到对象。[解析](https://github.com/caoke/js_basic/blob/master/vue%E4%B8%ADObject.defineProperty%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%8D%E8%83%BD%E7%9B%91%E5%90%AC%E6%95%B0%E7%BB%84%E4%B8%8B%E6%A0%87.html)

42. ts 有哪些类型，ts 中想要过滤一些属性改怎么去写， pick
    pick 过滤

43. $nextTick 原理 [解析](https://juejin.cn/post/6888227890618433549)

面筋

vue2 和 vue3 的区别
1、双向数据绑定， 一个是基于 object.defindproperType, 一个是 proxy + reflect
2、APi 从 optionsApi 转成 compositionApi
3、性能：较慢， 更快 支持 tree-shaking
4、支持 ts

key 的作用 用 index 改变 组件会不会重新渲染

父组件监听子组件的生命周期

父组件刷新子组件方法 [解析](https://blog.51cto.com/u_15127533/3945393)

数据改变 视图不刷新 怎么排查 解决

wepack loader

options 请求 复杂请求 简单请求

offsetHeight 会不会触发 重绘 回流 [解析](https://segmentfault.com/a/1190000017329980)

image 480 宽度 加属性设置成 300 宽度

文字溢出点点点

对象锁定不让修改 object.freeze

es6 箭头函数 和普通函数区别 arguments 怎么替代

深拷贝 循环引用， 如果 JSON.string, JSON.parse 无法使用的时候，要怎么深拷贝[解析](https://juejin.cn/post/6844903998823088141)
用 map 处理
Map WeakMap 区别
weakMap 只接受 对象作为对名

Event Loop 和 JS 引擎、渲染引擎的关系 [解析](https://www.jianshu.com/p/afbbc65d2530)

dom 修改是同步还是异步 [解析](https://segmentfault.com/a/1190000018431703)

延迟 3 秒执行 用 settimeout setInterval 哪个好 线程角度 [解析](https://juejin.cn/post/6959777879680876575)

mixin 的 data, 生命周期，在混入的时候， 如果 有函数同名，用哪个， 生命周期的话 会怎么走

/deep/ 属性穿透的实现 [解析](https://qdmana.com/2022/02/202202241631271394.html)

for in 和 for of

国双

5.element ui 业务组件 封装

6.element ui 人员选择器组件 为什么需要进行二次封装

7.自定义组件获取为定义的 props

8.vue 作用域插槽 slot-scope

9.v-model 原理

10.自定义组件 v-model

11.data 数据变成不是响应式
object.freeze()
12.vue-router 路由有哪些钩子

13.beforeEnter 参数改变 会不会触发

14.组件获取路有参数

15.组件和路由解耦

16.虚拟列表的实现

17.权限中台开发中有没有遇到过什么困难，以及怎么解决的。

18.前端 创建 cookie 删除 cookie
document.cookie , 设置 expires 过期
19.scrollIntoView

20.浏览器各种宽高

21.sessionStoreage & localstoreage ------> https://www.icode9.com/content-4-1310317.html

22.session localstorage 跨域

23.跨域问题 怎么解决 请求头字段

24.absolute relative 定位的区别

25.rollup webpack 区别

26.迭代器

27.?? 操作符

28.什么是可迭代对象

29.什么是 postcss

axios 怎么取消请求

为什么 setTimeout(() => {}, 3000) 会在 3s 后触发

一个项目设计：PC 端二维码，手机端扫码，服务端怎么通信，整个设计思路大概是什么样，二维码是后端生成还是前端生成。

微众银行 一面：

1.  事件循环

2.  this 指向

3.  import / require 的区别[解析](https://segmentfault.com/a/1190000021911869)
CommonJs 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。
CommonJs 模块是运行时加载，ES6 模块是编译时输出接口。

4.  实现一个 Object.assign 功能 考虑 多层级嵌套问题 对象多级层级嵌套 （assign 浅拷贝）

5.  vue3 ---> computed 、reactive、slots 实现原理 （居然没问 diff ？？？？）

6.  tailwindCss 有没有接触过。

7.  typescript 装饰器、类型 元祖类型数据怎么转化成对象 github 类型体操第 11 题。

平安人寿 一面

flex: 1 的具体内容 ， flex: flex-grow flex-shrink flex-basis (放大，缩小，占有空间)

虚拟列表

事件循环，event Loop

宏任务和微任务有哪些

弹性盒模型，

dom 事件流，

事件委托

金蝶 快递 100 二面

1，rem 是怎么计算 2， http 状态码 3， 首页白屏优化， 4 CSS 优化，5，开发过程中，与 UI，前后端怎么去协同开发。

平安 4 面

离职的原因是什么？

薪酬结构核福利待遇。（14 \* 13 薪吗？）

目前的职级等级是什么？

你来平安这边以后，你的期望薪资是什么？

总包、或者薪资结构你这边是怎么考虑的，谈谈你的想法？

有具体的薪资值？(总包 20 是吧？)

毕业以后 你参加工作以后 有哪个项目让你最满意，最有成就？

权限中台这个项目中你所担任的角色是什么？

目前你的工作年限 3 年，如果对你的技术水平打分，给自己打几分？

未来几年的技术方向的规划？

谈一谈自己的优势以及对自己的认知的不足？

平时自我提升的方法、途径。

平常业余时间除了敲代码以外，有什么个人的兴趣爱好？

为什么会选择我们平安作为下一份工作？

个人对加班的看法？

你这边如果确定 offer 以后，这边需要多久时间可以到岗？(两到三周)Other , 计算一个区间的重合 V3 的传值方式

slot 插槽

TCP 为什么三次握手。三次握手的内容

四次挥手

V2 中数组的监控

生命周期中的一些 this。

路由守卫中的 this. beforeRouteEnter， 这个时候是没办法拿到实例的

script 的异步 defer 标签

微众

多线程 -- 时间切片

webpack 生命周期
