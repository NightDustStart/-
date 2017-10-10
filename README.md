# -
2018前端面试题整理 及答案
#说明：前面有过的后面不在重复

# 通用

1. 自我介绍
2. 项目介绍
3. 问面试官问题
4. 项目遇到的问题
5. 实习内容

div + p  所有紧邻div的p元素 
div ~ p  前面有div的所有p元素

# 滴滴

1. 快速排序
	* 见算法.js
2. react生命周期 == Vue生命周期
	* new Vue()
	* <font style="color: red;">beforeCreate事件钩子</font>
	* 监控Data对象数据变化 --> init Events 初始化内部事件
	* <font style="color: red;">created事件钩子</font>
	* 检测是否绑定了el 如果没有则停止 等待绑定el
	* 判断是否具有template 是->按照template模板生成rander函数，否-> 按照外部html模板与data相结合
	* <font style="color: red;">beforeMount挂载钩子</font>
	* 将上面变编译好的hml内容替换el属性指向的Dom对象里面的内容
	* <font style="cotlor: red;">Mounted挂载钩子</font>
	* 进入数据实时监控
	* data 变化前触发 beforeUpdate 更新完成 Updated
	* 销毁前 beforeDestroy 
	* 接触watchers，子组件，事件监听
	* 销毁完成 Distoryed 
3. diff算法，为什么从n^3降低到n  --> <a herf = "https://zhuanlan.zhihu.com/p/20346379?refer=purerender">源码解析</a>
	* 传统diff算法使用循环递归的方法来进行比较，时间复杂度达到了O(n^3)
	* vue react 把它进行了优化,分为三个层面
	* tree diff  两棵树只进行同级比较
	* component diff
	* element diff 加入key 把节点的插入删除改编为节点的移动 
4. canvas dragImages fillText 高斯模糊
  * <a herf = "http://www.webxuhao.com/2017/05/10/html5_canvas/">见博客</a>
5. 跨域 jsonp cors postMessage
	* <a herf = "http://www.ruanyifeng.com/blog/2016/04/cors.html">cors阮一峰</a>
	* postMessage(data,url);    监听message事件
6. http 请求头里面包含什么，以及请求行 请求主体
	* 请求行  方法（GET,POST），URL，HTTP版本，
	* 请求头  http首部字段   
	  * Cache-Control 控制缓存行为
	  * Data 创建报文的日期时间
	  * Connection 1.控制不在转发的首部字段2.管理持久链接
	  * If-Match 比较实体标记(E-Tag)
	  * If-Modified-Since 比较资源更新时间
	  * Referer 标记URL的请求方
	* 请求主体 我们传递的一些数据 例如 name=xuhao&password=1234&....
7. webpack 如何使用？
	* <a href="http://www.jianshu.com/p/42e11515c10f#">webpack入门-简书</a>
8. koa2 async await 同步还是异步 使用方法
	* 异步的
	* <a href="https://cnodejs.org/topic/5640b80d3a6aa72c5e0030b6">async await</a>
	* ```javaScript
		var sleep = function (time) {
			return new Promise(function (resolve, reject) {
				setTimeout(function () {
					resolve();
				}, time);
			})
		};
		var start = async function () {
			// 在这里使用起来就像同步代码那样直观
			console.log('start');
			await sleep(3000);
			console.log('end');
		};
		start();
	* 规则
	  * async 表示这是一个async函数，await只能用在这个函数里面。
	  * await 表示在这里等待promise返回结果了，再继续执行。
      * await 后面跟着的应该是一个promise对象（
	* <a herf="https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434501579966ab03decb0dd246e1a6799dd653a15e1b000">廖雪峰Koa2</a>
9. jquery extends原理
	* $.extends(Object);把obj的方法扩展(浅克隆)
	* $.extends(target,origin);(浅拷贝)
	* $.extends(boolean,Object);(深拷贝)
	* 首先判断先参数个数，再根据第一个参数来判断是否是浅拷贝还是深拷贝
10. 深层克隆，浅层克隆
	* 同上
11. 数组检测 
	* instanceof  当一个页面把arr 传入iframe时 无法保证结果正确 
	* constructor 可以被重写 不准确
	* Array.isArray  新方法 有一定兼容性问题
	* Object.prototype.toString.call(arr);"[Object Array]"
12. ES6箭头函数和普通函数的区别
	* 箭头函数是没有this的，在箭头函数里面console.log(this),打印的一直都是沿着作用域向上查找的this。之所以就不能作为构造函数
	* 箭头函数更加纯粹，更加适合函数式编程
	* 不能作为构造函数
#另一个

1. 判断数组对象检测
  * 上面说过 
2. vue双向数据绑定
  * 有一个watcher 劫持Object.definedProperty.getter/setter发生变化 随之更新视图
  * 反过来当在视图(如input)输入数据时，也会触发订阅者watch，更新最新的数据到data里面(图中的a.b),这样model数据就能实时响应view上的数据变化了，这样一个过程就是数据的双向绑定了。
3. 继承-> 原型链 构造函数
	* 圣杯模式 借用空函数来隔离target函数 和 origin函数
	* 原型是函数的一个属性，它定义的这个函数作为构造函数分共有祖先
	* 构造函数 首先1. 隐式的创建一个this对象 2. 然后把函数作用域给this 3. 然后执行函数内部代码 4. 返回this
4. 设计模式
  * 整理单独一篇
5. ES6 rest参数 arguments
  * ... 使用iterater 遍历
#另一个 

1. 单项数据流--> vuex
  * state，驱动应用的数据源；
	* view，以声明方式将 state 映射到视图；
	* actions，响应在 view 上的用户输入导致的状态变化。
2. 双向数据流
  * 同双向数据绑定
3. this指向
	* 
4. 闭包
	* 
5. EA6的 class类的概念  和原型的区别
	* 语法糖 底层还是有原型链继承实现的
# 京东

1. 输入URL发生什么
	* 浏览器通过DNS解析获得资源IP地址
	* 客户端通过tcp/ip协议发送http请求协议包 与服务器建立连接，并发起资源请求
	* 服务端响应请求，发送http应答包
	* 客户端与服务端断开连接，随即开始处理数据
2. null  undefined  null == undefined
3.  ==   ===
4. ajax
	* ```javascript		 
		function AJAX(json) {
			var url = json.url,
				method = json.method || "get",
				flag = json.flag,
				data = json.data,
				callBack = json.callBack,
				xhr = null;
			if(window.XMLHttpRequest) {
				xhr = new window.XMLHttpRequest();
			}else {
				xhr = new ActiveXObject('Mircosoft.XMLHTTP');
			}			
			if(method == 'get') {
				url += '?' + data + new Date().getTime(); 
				xhr.open('get', url, flag);
			}else {
				xhr.open('post', url, flag);
			}
			xhr.onreadystatechange = function () {
				if (xhr.readyState === 4 && xhr.status === 200) {
					// 数据已经可用了
					callBack(xhr.responseText);
				}
			}
			if(method == 'get') {
				xhr.send();
			}else {
				xhr.setRequestHeader('Content-Type', 'application/x-www-form-urle');
				xhr.send(data);
			}	
		}

# 58

1. 笔试题（大题）
2. jsonp
3. 解析url参数
	* ```javascript
		var str = "?name=xuhao&id=1&pass=meme";
		function Url(key){
			if(str.indexOf('?') !== -1){
				str = str.substr(1); //截取字符串 去掉?
				arr = str.split("&");
				for(var i = 0; i < arr.length; i++){
					item = arr[i].split("=")
					if(key == item[0]){
						return item[1];
					}
				}   
			}
		} 
4. smarty PHP 模板引擎
5. Dom操作
	* 选择DOM元素
		* document.getElementById
		* document.getElementsByClassName  IE8以下没有
		* document.getElementsByTagName
		* document.getElementsByName  部分name会生效
		* hasChildNodes()可以检测是否有子节点
		* parentNode 查找父节点
		* childNodes 子节点们
		* firstChild 第一个子节点
		* lastChild 最后一个子节点
		* nextSibling 下一个兄弟节点
		* previousSibling 上一个兄弟节点
		* parentElement 返回当前元素的父元素节点
		* children 所有子元素节点
		* nextElementSibling 下一个兄弟节点
		* previousElementSibling 下一个兄弟节点
		* document.creatElement()
		* document.creatDocumentFragment
		* appendChild(child);
		* insterBefore(a, b) 把a插在b前面
		* replaceChild(new,old);
		* innerHTMl/innerText
		* ele.setAttribute('id', 'demo');
		* ele.getAttribute('id', 'demo');

6. zepto jquery 事件委托区别
  * zepto在代码解析的时候，所有document的所有 click 委托事件都依次放入一个队列里，click 的时候先看当前元素是不是.a，符合就执行，然后查看是不是.b，符合就执行。
	* jquery document上委托了2个 click 事件，click 后判断是否当前符合条件（选择符），然后把事件拿出来执行。
7. bind apply call 区别
8. 死锁
	* 死锁是指两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程称为死锁进程。
9. 数组去重 多种  hash set indexOf
10. 浏览器解析页面过程 浏览器层面优化页面显示速度
	* 详见js时间线 以及性能优化
11. 三个请求 前两个成功执行 第三个 设计一个方案 可以打印出ajax参数 和返回数据
12. http与缓存有关字段
  * Expires、Cache-Control、Last-Modified、 ETag

# 大疆

1. 页面性能优化问题
2. 移动端适配 
	* 顶宽-高度还原设计稿
	* rem  html font-size js控制根据不同的宽度来计算font-size大小
	* flex布局
	* rem 原理
		* 
3. http缓存字段
4. 类似小说分页问题
5. 一个数组 里面重复的数大于一半  最快的找出这个数
6. 介绍vuex，为什么使用vuex 好在哪里 
7. vue-router 前端路由比后端路由 好在哪里
8. tcp / udp  

# 美团

1. 设计模式 （重复）
2. 面向对象
3. ES6
4. promise 设计原理 为什么好 
5. 封装promise 的AJAX
6. 弹性盒子
7. H5音频种类 
8. 解决动画卡顿
9. 线程进程
10. 链表 二叉树
11. 排序算法
12. http https 
13. http 不使用 websocket 实现长连接  keep-live

# 无名

1. 原生实现call apply new
2. 事件委托的机制的原理
3. 移动端的兼容性bug
4. rem 的兼容性  计算方式
5. 数组去重 遇见function怎么办
6. bfc原理
7. 链表数组的区别
8. 排序哪个更快
10. 对前端框架的理解
11. 线程有哪些状态
12. js线程机制
13. 前端处理比较耗时间的操作

# 人人

1. break能否终止forEach循环
2. Object.assign
3. ovflow 
4. em 相对于父级字体的大小 rem相对于html(根标签)
5. for in 不能遍历原型链属性  使用hasOwnsPrototype()来鉴别是不是自己的属性
6. 100000 -> 100.000

#  百度外卖一面（一）

1. xml和XHTML有什么区别
	* html 不区分大小写  xml区分
	* html 固有标记 xml 自己定义标签 可以扩展
	* html是用来显示数据的， xml是用来展示数据存放数据的， 
	* xml 是一种跨平台的 与软硬件无关的，处理和传输信息的工具
2. css有哪些选择器
	* 标签
	* 类
	* id
	* 通配符
	* 父子
	* 兄弟
	* css3 伪类 nth-of-type()
3. 什么是事件委托
4. 用过回调函数吗? 在哪里用到？为什么用到？
 * AJAX
 * 图片预加载
 * 需要异步的时候
5. 写一下拖拽函数？拖动过快，bug如何解决？
	* 把事件注册在document上 然后使用e.target
6. 引入css样式的几种方式
	* link
	* style
	* @import
7. 如何获取后台数据？怎么样和后台进行交互？
	* AJAX
8. 了解node.js吗？
9. 了解bootstrop框架吗
10. webpack能用来干什么?
	* 是一种模块化打包工具
	* 在webpack中一切都是模块
	* 把项目当做整体，通过一个主文件index.js根据配置信息 找到你的项目的所有依赖，并使用loader处理他们 最后打包成一个（或多个）浏览器是识别的文件
	* common.js 规范
11. 了解js吗？
12. 性能优化有哪些办法？
13. 怎么让页面快速渲染？
14. 元素的分类？
	* 块级元素
	* 行级元素
15. IE6浏览器bug怎么解决？
16. H5有哪些新特性？
	* 语义化标签
	* audio/video
	* canvas svg
	* drag
	* postMessage
	* 离线缓存
17. 后台给浏览器一个数据怎么解析？
	* JSON.parse
	* JSON.stringify
18. jquery是怎么用的?
19. 强制类型转换？隐式类型转换都有什么？
	* Number String boolean 
	* 隐式类型转换 
		* isNaN
		* 递增递减操作符（包括前置和后置）、一元正负符号操作符
		* \+ \- \* \/ 
		* & || !
		* \> \< \>= \<= \==
#  百度外卖一面（二）

1. 如何获取元素的宽度？
  * 下面有
2. 怎么判断一个元素是另一个元素的父级？
	* parent.Node 然后判断 nodeType 元素节点是1
	* parentElement 
3. 封装方法 将10进制转为64进制？
	* parseInt(num,radix) 把num 作为radix进制转换为10进制
	<!-- * ```javascript -->

4. 二叉树 中序
	* 按照键值大小排序
5. 怎么不用递归实现二叉树？（用栈）
6. rem
	* 以上有
7. 背包问题，动态规划？
8. 52张牌 随机发给4个人？
9. position sticky的浏览器兼容问题
	* 粘性定位
	* 使用Fixed-sticky库
10. 浏览器一横放4个正方体 宽随浏览器适应
	* wrapper 100%; 正方体浮动25%;
	* flex flex-grow:1;
# 百度外卖二面

1. 了解二叉树吗？
2. 用原生的方法获取元素宽度？
	* 视口尺寸
		* window.innerHeight
		* doucment.documentElement.clientWidth
	* 元素尺寸
		* dom.offsetWidth/dom.offsetHeight
		* el.getBoundingClientRect()
		* 通过元素top left bottom right 来进行计算
3. 手写jsonp
4. 手写ajax
