<h2>Vue.js 2.4.4版本，源码解读</h2>

<a href="https://github.com/terribleness/vue-read/issues/2" target="_blank"><h2>Vue运行时---第一步扩展实例方法</h2></a>
Vue扩展实例方法流程为：
1、	定义function Vue()
2、	initMixin扩展vm._init
3、	stateMixin扩展vm.$data、vm.$props、vm.$set、vm.$delete、vm.$watch
4、	eventsMixin扩展vm.$on、vm.$once、vm.$off、vm.$emit
5、	lifecycleMixin扩展vm._update、wm.$forceUpdate、vm.$destroy
6、	renderMixin扩展vm.$nextTick、vm._render和一些工具方法
