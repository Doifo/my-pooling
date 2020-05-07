#### Vue生命周期

#### Vue动态参数

```
<a v-bind:[attributeName]="url"> ... </a>
<a v-on:[eventName]="doSomething"> ... </a>
```

#### Vue修饰符

```
事件
.stop
.prevent
.capture
.self
.once
.passive

按键
<input v-on:keyup.enter="submit">
按键码

系统
.ctrl
.alt
.shift
.meta
<!-- Alt + C -->
<input v-on:keyup.alt.67="clear">

<!-- Ctrl + Click -->
<div v-on:click.ctrl="doSomething">Do something</div>

.exact
<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button v-on:click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button v-on:click.ctrl.exact="onCtrlClick">A</button>

<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button v-on:click.exact="onClick">A</button>

鼠标
.left
.right
.middle

表单
.lazy
.number
.trim
```

#### Vue computed methods watch

computed：计算属性是基于它们的响应式依赖进行缓存的，只在相关响应式依赖发生改变时它们才会重新求值。依赖不变，computed会返回之前的计算结果。

methods：每当触发重新渲染时，调用方法将总会再次执行函数。

watch：当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

#### Vue v-for

```
object: {
      title: 'How to do lists in Vue',
      author: 'Jane Doe',
      publishedAt: '2016-04-10'
}
    
<div v-for="(value, name, index) in object">
  {{ index }}. {{ name }}: {{ value }}
</div>
```

#### Vue 组件data

一个组件的 data 选项必须是一个函数，因此每个实例可以维护一份被返回对象的独立的拷贝，data是一个函数时，每个组件实例都有自己的作用域，每个实例相互独立,不会相互影响。

#### Vue组件

```
全局注册
Vue.component('',{
    
})

基础组件自动全局注册
```

#### Property 与 Attribute 的差别

1、Attribute 对象包含标签里定义的所有属性，Property 只包含 HTML 标准的属性，不包含自定义属性（eg: data-xxx）。

2、Attribute 里的属性的值是 html 标签上原始的值，除非使用 setAttribute() 方法更改，不会根据用户输入而改变（eg: input 标签）。Property 在页面初始化时会映射并创建 Attribute 对象里的标准属性，从而节点对象能以对象的访问方式获取标准属性。在用户输入内容修改了原始值后，Property 里对应的属性会随之变化。即，查看原始值使用 Attribute，查看最新值使用 Property。（input 的 value 值也可以通过 input.defaultValue 查看原始值）

3、Property 与 Attribute 的某些属性名称是完全一样的，例如 ref, id ；某些名称有些轻微差别，例如 Attribute 里的 for、class 属性映射出来对应 Property 里的 htmlFor、className；某些属性名称一样，但是属性值会有限制或者修改，不会完全一样，相关的属性有 src, href, disabled, multiple 等。

#### Vue .prop

将属性名绑定到property上

#### Vue key

key的作用主要是为了高效的更新虚拟DOM。另外vue中在使用相同标签名元素的过渡切换时，也会使用到key属性，其目的也是为了让vue可以区分它们，否则vue只会替换其内部属性而不会触发过渡效果