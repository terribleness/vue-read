<h2>Vue.js 2.4.4版本，源码解读</h2>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/2" target="_blank"><h3>Vue运行时---第一步扩展实例方法（链接）</h3></a>
<p>Vue扩展实例方法流程为：</p>
<p>1、	定义function Vue()</p>
<p>2、	initMixin扩展vm._init</p>
<p>3、	stateMixin扩展vm.$data、vm.$props、vm.$set、vm.$delete、vm.$watch</p>
<p>4、	eventsMixin扩展vm.$on、vm.$once、vm.$off、vm.$emit</p>
<p>5、	lifecycleMixin扩展vm._update、wm.$forceUpdate、vm.$destroy</p>
<p>6、	renderMixin扩展vm.$nextTick、vm._render和一些工具方法</p>

<a style="text-decoration: underline;" href="https://github.com/terribleness/vue-read/issues/3" target="_blank"><h3>Vue运行时---第二步扩展静态方法（链接）</h3></a>
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
