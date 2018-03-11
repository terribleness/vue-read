<h1>Vue.js 2.4.4版本，源码解读</h1>

<h2>提纲分为这五章：</h2>
<h3>1、Vue构造函数：实例方法和静态方法</h3>
<h3>2、Vue的响应原理：Observe、Watcher、Dep关系</h3>
<h3>3、Vue的编译过程：template、AST、Render过程</h3>
<h3>4、Vue的虚拟节点：VNode、patch算法</h3>
<h3>5、Vue的异步队列：nextTick调度</h3>

<br/>
<img src="https://user-images.githubusercontent.com/37056647/37242039-a257ca6c-249d-11e8-9fca-a86d504c6dfe.png"/>
<br/>
<br/>
<h2>一、Vue构造函数：实例方法和静态方法</h2>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/2" target="_blank"><h3>Vue运行时---第一步扩展实例方法（点击链接）</h3></a>
<h4><span style="color:red;">总结</span>Vue扩展实例方法流程为：</h4>
<p>1、	定义function Vue()</p>
<p>2、	initMixin扩展vm._init</p>
<p>3、	stateMixin扩展vm.$data、vm.$props、vm.$set、vm.$delete、vm.$watch</p>
<p>4、	eventsMixin扩展vm.$on、vm.$once、vm.$off、vm.$emit</p>
<p>5、	lifecycleMixin扩展vm._update、wm.$forceUpdate、vm.$destroy</p>
<p>6、	renderMixin扩展vm.$nextTick、vm._render和一些工具方法</p>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/3" target="_blank"><h3>Vue运行时---第二步扩展静态方法（点击链接）</h3></a>
<h4><span style="color:red;">总结</span>Vue扩展静态方法流程为：</h4>
<p>1、扩展了工具方法Vue.util.warn、Vue.util.extend、Vue.util.mergeOptions、Vue.util.defineReactive</p>
<p>2、扩展了Vue.set 、Vue.delete、Vue.nextTick</p>
<p>3、扩展了Vue.options.conponents、Vue.options.directives、Vue.options.filters</p>
<p>4、扩展了Vue.options._base 等于 Vue构造函数本身</p>
<p>5、扩展了Vue.options.components为默认{name、abstract、props、created、destroyed、watch、render}对象</p>
<p>6、initUse（Vue）扩展了Vue.use</p>
<p>7、initMixin（Vue）扩展了Vue.mixin</p>
<p>8、initExtend（Vue）扩展了Vue.cid属性和Vue.extentd方法</p>
<p>9、initAssetsRegisters（Vue）扩展了Vue.componet、Vue.directive、Vue.filter三个方法</p>
<p>10、‘core/index’中扩展了Vue.$isServer和Vue.$ssrContext的get方法</p>
<p>11、‘runtime/index中扩展了’Vue.config的配置方法mustUseProp、isReservedTag、isReservedAttr、getTagnamespace、isUnknownElement</p>
<p>12、‘runtime/index’中使用了平台相关的指令和组件覆盖之前生成的Vue.options.directives和Vue.options.components</p>
<p>13、‘runtime/index’中增加实例方法vm.patch</p>
<p>14、‘runtime/index’中扩展了实例方法vm.$mounted</p>

<br/>
<br/>
<br/>
<h2>二、Vue的响应原理：Observe、Watcher、Dep关系</h2>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/4" target="_blank"><h3>Vue的响应原理：Observe、Watcher、Dep关系（点击链接）</h3></a>
<p>1、	每个data中属性元素会有一个闭包Dep的实例，里面存放Watcher实例</p>
<p>2、	当template编译为render函数时，会调用属性的get方法，将每一次调用都生成一个watcher实例，并压入dep中，产生订阅效果。</p>
<p>3、	当设置data中属性值的时候，调用属性的set方法通知所有订阅该属性的元素更新</p>
<p>4、	而且props，computed，watch内同理是增加watcher产生订阅和发布的效果。</p>
<br/>
<br/>
<br/>
<h2>三、Vue的编译过程：template、AST、Render过程</h2>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/5" target="_blank"><h3>Vue的编译过程：template、AST、Render过程（点击链接）</h3></a>
<p>1、	template先判断是否存在render函数，如果不存在则判断template模板，最后判断el标签。</p>
<p>2、	const ast = parse（template.trim(),options）是生成抽象语法树。</p>
<p>3、	optimize（ast,options）优化AST树。</p>
<p>4、	const code = generate(ast, options)这一句之后，生成render函数。</p>

<br/>
<br/>
<br/>
<h2>三、Vue的虚拟节点：VNode、patch算法</h2>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/6" target="_blank"><h3>①Vue的虚拟节点Vnode过程（点击链接）</h3></a>
<p>清晰描述了“tempalte”转化为“ast抽象语法树”转化为“render函数”转化为“vnode虚拟树”的过程。</p>
