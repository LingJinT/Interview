# 面试整理合集

## 一、HTML
### 1.什么是怪异模式？
为了兼容旧浏览器而产生的一系列怪异行为。
### 2.defer和async两个属性各有什么作用？
defer：立即下载，延迟执行，将在文档解析完之后执行，能保证执行顺序；
async：立即下载，异步执行，将边执行边解析文档，不能保证执行顺序。
### 3.什么是Shadow DOM?
我理解就是一个封闭的DOM元素，内部的脚本和样式不会对外部产生影响。
### 4.元素属性src和href有何区别？
src一般用作外部资源的地址，href一般是超链接的地址。
### 5.CSS有几种引入方式？它们有哪些区别？
- 内联样式：直接写在元素上，方便直观，但是不易维护，优先级最高。
- style标签：直接写在文档的style标签中，与元素分离，易于维护，优先级中。
- link导入：与html文档分离，方便复用，优先级最低。
### 6.JavaScript有几种引入方式？它们有哪些区别？
- script标签内：直接写在html中的script标签内，方便直观，但是不易复用和维护。
- script标签导入：利用scr指向外部文件，方便复用。
- 动态导入：利用js脚本动态导入script标签，可以减小体积，按需加载。
### 7.嵌入在HTML文档中的图像格式有哪些，都有些什么特点？
- jpeg: 支持有损压缩，文件体积比png小。
- png：支持无损压缩，支持透明度，文件体积较大。
- svg：基于XML的矢量图形，放大缩小不会失真，体积也小。
- gif：支持动画，体积较大。
- webp：同时支持透明度和动画，压缩率也比jpeg、png、gif好。
### 8.HTML5的新特性
- 语义化标签。
- web存储。
- video、radio。
- 拖拽。
- canvas。
- Web Workers、Web Sockets。
- 新的表单控件属性。

## 二、样式
### 1.请谈谈你对BFC的理解？
#### 1）什么是BFC
块级格式化上下文,内部的布局不会影响外部。
#### 2）BFC 有什么用
- 解决外边距塌陷。
- 解决浮动高度塌陷。
- 独立容器。
#### 3）如何触发
- flex、inline-block布局。
- position: absolute、fiexed。
- float: left、right。
### 2.谈谈CSS预处理器？
#### 1）为什么需要用预处理器
让用户更方便地写css，使其更易维护，更有效率。
#### 2）CSS 主要有哪些预处理器、其优缺点有哪些？
- postcss：将css解析成ast树，方便其他处理器处理。
- less：提供嵌套、混合、变量、继承等功能，不支持自定义函数。
- sass：提供嵌套、混合、变量、自定义函数等功能。
- css module：提供作用域隔离
- css in js：灵活、组件隔离，但是体积较大
- tailwind css：快速开发、一致性，但是需要学习成本 class类较长

### 3.实现元素的水平垂直居中？
#### 1）flex
```css
display: flex;
justify-content: center;
align-items: center;
```
#### 2）grid
```css
display: grid;
justify-content: center;
align-items: center;
```
#### 3）相对定位
```css
position: relative;
display: inline-block;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
```
#### 4）绝对定位
```css
position: absolute;
 top: 50%;
left: 50%;
transform: translate(-50%, -50%);
```
#### 5）line-height
```css
height: xxx;
line-height: xxx;
text-align: center;
```
### 4.CSS3的新特性？
- 新的选择器
- 圆角边距
- 阴影
- flex
- grid
- 过渡和动画
- 媒体查询
### 5.什么是盒模型？
content、padding、border、margin
### 6.什么是外边距塌陷？
两个相邻的外边距重叠会取其大的一边。
### 7.CSS中的过渡与动画有哪些区别？
- 过渡：静态的，比较简单
- 动画：动态的，相对复杂
### 8.如何实现一个圣杯布局？
display:flex，两边固定宽度，中间flex：1

## 三、基础
### 1.闭包的作用和原理
#### 1)什么是闭包
内部能访问外部函数内部的作用域，即使外部函数已经执行完毕
#### 2)闭包的应用
- 模块化
- 定时器
- 监听器
- 等等回调函数
### 2.前端模块化规范
#### 1)JavaScript 主要有哪几种模块化规范
- commonjs：node中的模块化规范，因为其不支持异步加载所以在浏览器中不适用。
- AMD：支持异步加载，推荐依赖前置，语法复杂，无法静态分析模块。
- CMD：支持异步加载，推荐依赖就近，语法复杂，无法静态分析模块。
- UMD：同时支持commonjs和AMD，代码量大。
- ESM：支持静态分析模块，兼容性较差。
#### 2)AMD / CMD 有什么异同
- AMD: 依赖前置
- CMD：依赖就近
#### 4)模块化解决了什么问题/痛点
代码复用、程序维护性、命名冲突等
### 3.ES5、ES6 如何实现继承
#### 1)原型链概念
一个实例的__proto__指向其constructor.prototype，这就可以让这个实例访问到它构造函数上面的一些方法，以此类推，如果这个构造函数是另一个对象的实例，那么也相应地继承，直到Object.prototype.__proto__ === null
#### 2)原型链继承
- 每个实例都共用一个对象
- 无法传递构造函数的参数
```js
function Child(name) {
  this.name = name
}
function Parent(age) {
  this.age = 16
}
Parent.prototype.say = function() { console.log('say') } 
Child.prototype = new Parent()
Child.prototype.constructor = Child
const child = new Child('zhangsan')
console.log(child.age)
```
#### 3)构造函数继承
- 实例不会共用一个对象
- 可以传递构造函数的参数
- 无法访问父亲的原型方法
```js
function Parent(name) {
  this.name = name
}
function Child(name) {
  Parent.call(this, name)
}
Parent.prototype.say = function() {
 console.log('say')
}
const child = new Child('zhangsan')
console.log(child)
```
#### 4)组合继承
- 可以访问父亲的原型方法
- Parent构造函数会被调用两次
```js
function Parent(name) {
  this.name = name
}
Parent.prototype.say = function() { console.log('say') }
function Child(name) {
  Parent.call(this, name)
}
Child.prototype = new Parent()
Child.prototype.constructor = Child
const child = new Child('zhangsan')
console.log(child)
```
#### 5)寄生组合继承
- 父亲的构造函数只用调一次
- 写法复杂
```js
function inhertPrototype(Child, Parent) {
  const prototype = Object.create(Parent.prototype)
  Child.prototype = prototype
  Child.prototype.constructor = Child
}

function Parent(name) {
  this.name = name
}
Parent.prototype.say = function() { console.log('say') }
function Child(age, name) {
  Parent.call(this, name)
  this.age = age
}
inhertPrototype(Child, Parent)
const child = new Child(16, 'zhangsan')
console.log(child)
```
#### 6)class继承
- 写法简单
```js
class Child extends Parent
```
### 4.New 操作符的原理
#### 1)new 操作符做了什么
- 创建一个对象
- 将构造函数的prototype指向该对象的__proto__
- 将this指向该对象
- 执行其构造函数
- 如果构造函数返回的值为空则返回这个对象，否则返回该值
#### 2)new 操作符的模拟实现
```js
todo
```
### 5.JavaScript 异步编程
#### 1)JavaScript 异步编程方案有哪些,各有什么优缺点？
- 回调函数: 容易产生回调地狱
- promise: 解决了回调地狱的问题，但是无法触发多事件处理
- generator: 语法复杂
- async await: 同步写法，便于阅读
### 6.TypeScript 中的 Interface 和 Type Alias的区别
- Interface可以声明合并
- type可以定义基本类型
### 7.什么是 TypeScript 泛型,其作用是什么
动态类型
### 8.谈谈ES6新特性
- 箭头函数
- let、const
- 模块化
- promise
- 解构赋值
- 模板字符串
- 类和继承
### 9.箭头函数和普通函数的区别
- 箭头函数的this指向函数外部
- 箭头函数没有arguments
### 10.深浅拷贝
#### 1) 引用类型、基本类型
基本类型存储在栈中，引用类型存储在堆中，栈中放对应的指针。
#### 2) 深浅拷贝的区别
浅拷贝就是只对象的第一层，如果对拷贝对象修改第二层中的引用类型，原对象也会受到影响，深拷贝则原对象不会受到影响。

## 四、浏览器
### 1.浏览器的跨域
#### 1)什么是跨域
不同域名下的访问
#### 2)为什么会跨域
浏览器专门设置的安全策略，防止网页遭受攻击
#### 3)怎么解决跨域
- CORS：后端设置Access-Control-Allow-*。
- 反向代理：通过配置反向代理服务，请求相同的域名，根据规则转发到实际的服务地址。
- JSONP：通过script标签没有跨域限制的机制，前后端一起修改，较复杂，不推荐。
### 2.浏览器的重排重绘
#### 1)哪些行为会引起重绘
外观属性变更，比如color，opacity等
#### 2)哪些行为会引起重排
尺寸、位置变更，比如：height、width、position、获取布局信息等
#### 3)如何提升页面渲染性能
- dom批量更新
- 缓存布局信息
- 合理利用transform，开启GPU加速
### 3.浏览器的渲染机制
#### 1)浏览器如何渲染页面
- 解析HTML。
- 构建CSSOM树。
- 计算节点的大小及位置信息。
- 计算节点的分层信息。
- 提交给GPU进行渲染。
#### 2)有哪些提高浏览器渲染性能的方法
- script标签延迟加载
- 减少重绘重排
### 4.浏览器的垃圾回收机制
#### 1)什么是内存泄漏
该被回收的数据，没有被回收，导致内存占用越来越高。
#### 2)常见的垃圾回收算法
- 老生代算法：标记-清除算法，把引用到的数据打上标记，清除没有标记的数据，再重新整理。
- 新生代算法：将空间一分为二，如果数据被引用则放入b空间，否则直接释放，最后a、b空间翻转，以此循环。
#### 3)如何排查内存泄漏
- 内存快照
- 性能指标
### 5.浏览器的事件循环
#### 1)什么是浏览器事件循环
js是单线程机制，所以分为了微任务和宏任务，一个宏任务执行完后，会优先去清空微任务队列，再执行下一个宏任务。
#### 2)浏览器为什么需要事件循环
支持单线程中的异步任务，当发生异步任务的时候，将该任务挂起，等到时机再执行其回调任务。
### 6.前端路由实现原理
#### 1)路由是什么
一个path对应一个页面
#### 2) 前端路由的实现方式和实现原理
- hash路由监听hashchange事件，当其改变的时候切换其组件显示。
- history路由监听popState事件，当其改变的时候切换其组件显示。
#### 4) 前端路由的优势
- 切换路由无刷新
- 减轻服务端压力
#### 5) 前端路由的不足
- SEO不友好
- 初次加载时间长
### 7.本地存储方式及场景
#### 1) cookie、Web Storage 以及 IndexedDB 区别
- cookie: 请求携带，4kb
- localStorage：持久化存储在本地，5mb，
- sessionStorage：临时性存储在页签，5mb
- IndexDB：大存储

## 五、框架
### 1.React Hooks 实现原理
#### 1)React Hooks 是什么
react 16.8引入的新特性，使函数组件也可以使用state
#### 2)React Hooks 是怎么实现的
```js
todo
```
#### 3)使用 React Hooks 需要注意什么
- 只在函数组件中使用
- 在函数最顶层使用
### 2.常见框架的 Diff 算法
#### 1)虚拟 DOM 是什么
模拟真实dom创建出来的一个js对象。
#### 2)虚拟 DOM 的作用
- 增量更新dom节点，减少性能消耗
- 组件化开发
- 跨端开发
#### 3)讲一下 Vue 的 Diff 算法
- 产生新旧虚拟dom树
- 深度优先遍历
- 利用双端比较算法进行比较，如果key不同则替换，如果类型不同则替换，如果相同则递归遍历子节点
- 根据差异一次性更新真实dom
### 3.HOC、Render Props、Hooks各自的优缺点
#### 1)什么是 HOC / Render Props / Hooks
- HOC：高阶组件，传入一个组件，返回一个增强后的组件，比如redux的connect
- Render Props: 把组件作为props传给另一个组件，复用数据，比如Table的render
- Hooks：可以在函数式组件中使用状态等
#### 2)为什么需要 HOC / Render Props / Hooks
- 提高代码复用性
- 增强可维护性
#### 3)Hooks 相比其他方案有什么优势
逻辑清晰，不存在回调地狱。
### 4.React Fiber 的作用和原理
#### 1)Fiber 是什么
react 16中采用的一种异步可中断更新机制
#### 2)谈谈你对 Fiber 的了解
- 对大型任务进行分片
- 对各个人物划分优先级，优先处理高优先级的任务
- 可以对分片执行挂起、恢复、终止等操作
#### 3)Fiber 对 React 的使用带来了什么影响
- react的更新过程可以理解为两个阶段：调度阶段、渲染阶段。在调度阶段找出虚拟dom的差异，在虚拟阶段进行渲染
- 浏览器一般都是60HZ，那也就是 1 / 60 大概是16ms
- 如果比较的树层级很深，超过16ms，那用户就会感觉卡顿
- 引入Fiber之后，可以对大型任务分片，使其可中断，这样就会有时间去处理其他任务，使用户感觉良好。
### 5.React 事件机制原理
#### 1)React 合成事件与原生 DOM 事件的区别
- 跨浏览器兼容性
- 事件处理优先级
- 性能优化，批量处理，减少重绘和重排
#### 3)React 事件如何解决浏览器兼容问题
- 事件属性放在target中
- 不同浏览器的事件，用统一API处理
### 6.谈谈 React 和 Vue 的区别
- 学习曲线：vue想降低学习门槛，react想灵活coding
- 社区生态：vue有全家桶，react社区根据需要自己选
- jsx与模板语法：模板语法可以关注点分离，jsx可以使组件化开发更灵活
### 7.Vue 的 computed 和 watch 的区别
#### 1)computed 和 watch 的实现原理
类似下面的数据劫持
#### 2)computed 和 watch 的适用场景
watch适合复杂场景
### 8.Vue 的数据绑定机制
#### 1)Vue 是如何实现数据劫持和双向绑定的
- 利用getter，收集依赖，注册监听器
- 利用setter，变动数据的时候执行监听器
#### 2)MVVM 是什么
- model：处理数据、业务逻辑
- view：更新视图
- modelView：连接上面两者

## 六、网络
### 1.HTTP/1.0、HTTP/1.1 和 HTTP/2 的区别
- HTTP1.0: 不支持持久连接，一次只能发送一个请求
- HTTP1.1: 支持请求并发，但是有队头阻塞问题
- HTTP2.0: 多路复用，无队头阻塞问题
### 2.前端安全
#### 1)常见的前端攻击
- XSS：脚本注入，比如从输入框中或者url中携带<Script xxx/>
- CSRF：伪造用户凭证，利用cookie会携带在请求中
#### 2)如何防范
- XSS：输入编码、输出编码、校验等。
- CSRF：增加CSRF token、检查头部的referer头部
### 3.HTTP 缓存机制
- 强缓存：Expires、Cache-Control设置资源过期时间
- 协商缓存：Last-Modified/If-Modified-Since对比资源上一次修改的时间、ETag/If-None-Match：对比资源内容是否发生变化
### 4.TCP的三次握手与四次挥手
#### 1)三次握手
- 客户端发送给服务端SYN
- 服务端发送给客户端SYN-ACK
- 客户端发送给服务端ACK
#### 2)四次挥手
- 客户端发送给服务端FIN
- 服务端发送给客户端ACK
- 服务端发送给客户端FIN
- 客户端发送给服务端ACK
## 工程化
### 1.webpack工作流程
- 初始化阶段：读取外部配置、创建构建对象compiler、注册插件等等。
- 构建阶段：执行compiler.run,得到compilation对象，根据入口文件，递归编译，得到最终模块产物和依赖关系图。
- 生成阶段：根据依赖关系图和最终模块产物生成文件并写入文件系统。
### 2.babel的原理
#### 1)Babel 是什么、作用是森么
babel是代码编译器、可以将js代码转换成AST树，便于其他插件对其处理，最终生成js的作用
#### 2)压缩代码如何实现
对AST树进行处理，比如处理if语句，移除debugger、console等，最后还可以利用插件的压缩算法进行压缩。
### 3.谈下 webpack loader 的机制
#### 1)webpack loader 是如何工作的
- normal流程：从后往前执行。
- pitch流程：先执行pitch，再从后往前执行，但是如果遇到某个pitch有返回值，则直接从这个loader往前执行
### 4.谈谈微前端
#### 1)为什么要用微前端
- 独立团队独立开发
- 渐进式重构
#### 2)微前端的优缺点
- 技术栈灵活
- 降低耦合性
- 提升维护性
- 增量升级、回退
- 性能不好
- 样式问题

## 七、编码
### 1.实现一个符合 Promises/A+ 规范的 Promise
### 2.实现节流防抖函数
### 3.将列表还原为树状结构
### 4.实现 apply/call/bind

## 八、算法
### 1.平衡二叉树
### 2.反转链表
### 3.二叉搜索树的第 k 大的节点
### 4.找到数组中重复的数字

## 九、综合
### 1.浏览器从输入网址到页面展示的过程
- 输入URL
- 解析DNS
- 建立TCP连接
- 客户端发送请求给服务端
- 服务端响应
- 客户端解析HTML
- 客户端渲染页面
### 2.多图站点性能优化
- 选择合适的图片：了解各图片的优缺点
- HTTP传输优化：base64、CDN、HTTP2等
- 加载策略优化：懒加载、预加载、雪碧图等等
### 3.如何减少白屏的时间
- HTTP传输优化：HTTP2、CDN、缓存等
- 打包体积优化：gzip、分包等
- 加载策略优化：路由懒加载、骨架屏、服务端渲染等
