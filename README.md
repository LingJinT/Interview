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
display: flex; justify-content: center; align-items: center;
#### 2）grid
display: grid; justify-content: center; align-items: center;
#### 3）相对定位
position: relative; display: inline-block; top: 50%; left: 50%; transform: translate(-50%, -50%);
#### 4）绝对定位
position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
#### 5）line-height
height: xxx; line-height: xxx; margin: auto;
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
- 什么是闭包
- 闭包的应用
### 2.前端模块化规范
- JavaScript 主要有哪几种模块化规范
- AMD / CMD 有什么异同
- ESM 是什么
- 模块化解决了什么问题/痛点
### 3.ES5、ES6 如何实现继承
- 关于 ES5 和 ES6 的继承问题
- 原型链概念
### 4.New 操作符的原理
- new 操作符做了什么
- new 操作符的模拟实现
### 5.JavaScript 异步编程
- JavaScript 异步编程方案有哪些
- JavaScript 异步编程方案各有什么优缺点
### 6.TypeScript 中的 Interface 和 Type Alias
- Interface 和 Type Alias 的作用
- Interface 和 Type Alias 的相同点
- Interface 和 Type Alias 的区别
### 7.什么是 TypeScript 泛型
- TypeScript 泛型的作用是什么
### 8.谈谈ES6新特性
### 9.箭头函数和普通函数的区别
### 10.深浅拷贝

## 四、浏览器
### 1.浏览器的跨域
- 什么是跨域
- 为什么会跨域
- 为什么有跨域限制
- 怎么解决跨域
### 2.浏览器的重排重绘
- 如何提升页面渲染性能
- 如何减少页面重排重绘
- 哪些行为会引起重排/重绘
### 3.浏览器的渲染机制
- 浏览器如何渲染页面
- 有哪些提高浏览器渲染性能的方法
### 4.浏览器的垃圾回收机制
- 什么是内存泄漏
- 常见的垃圾回收算法
- 如何排查内存泄漏
### 5.浏览器的事件循环
- 什么是浏览器事件循环
- 浏览器为什么需要事件循环
- Node.js 中的事件循环
### 6.前端路由实现原理
- 路由是什么
- 前端路由的实现方式和实现原理
- 前端路由和服务端路由的区别
- 前端路由的优势
- 前端路由的不足
### 7.本地存储方式及场景
- cookie 的优缺点
- cookie、Web Storage 以及 IndexedDB 区别

## 五、框架
### 1.React Hooks 实现原理
- React Hooks 是什么
- React Hooks 是怎么实现的
- 使用 React Hooks 需要注意什么
### 2.常见框架的 Diff 算法
- 虚拟 DOM 是什么
- 虚拟 DOM 的作用
- 讲一下 Vue 的 Diff 算法
### 3.HOC、Render Props、Hooks各自的优缺点
- 什么是 HOC / Render Props / Hooks
- 为什么需要 HOC / Render Props / Hooks
- 如何提高代码复用性
- Hooks 的实现原理
- Hooks 相比其他方案有什么优势
### 4.React Fiber 的作用和原理
- Fiber 是什么
- 谈谈你对 Fiber 的了解
- Fiber 对 React 的使用带来了什么影响
### 5.React 事件机制原理
- React 合成事件与原生 DOM 事件的区别
- React 如何注册和触发事件
- React 事件如何解决浏览器兼容问题
### 6.谈谈 React 和 Vue 的区别
- 相同之处
- 不同之处
### 7.Vue 的 computed 和 watch 的区别
- computed 和 watch 的实现原理
- computed 和 watch 的适用场景
### 8.Vue 的数据绑定机制
- Vue 是如何实现数据劫持的
- Vue 是如何实现双向绑定的
- MVVM 是什么

## 六、网络
### 1.HTTP/2 和 HTTP/1.1 的对比
- 了解 HTTP/2 吗
- HTTP/1.0、HTTP/1.1 和 HTTP/2 的区别
### 2.前端安全
- 如何防范 XSS / CSRF 攻击
- 说说 HTTPS 中间人攻击，及其如何防范
### 3.HTTP 缓存机制
- 了解浏览器的缓存机制吗
- 谈谈 HTTP 缓存
- 为什么要有缓存
- 缓存的优点是什么
### 4.TCP的三次握手与四次挥手

## 工程化
### 1.webpack工作流程
- webpack 工作流程是怎样的
- webpack 在不同阶段做了什么事情
### 2.babel的原理
- Babel 是什么
- Babel 有什么用
- 压缩代码如何实现
### 3.谈下 webpack loader 的机制
- webpack loader 是如何工作的
- 如何编写 webpack loader
### 4.谈谈微前端
- 为什么要用微前端
- 微前端的优缺点

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
### 2.多图站点性能优化
### 3.如何减少白屏的时间

