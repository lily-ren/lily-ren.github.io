---
title: vue
tag: vue全家桶
---
#### vue学习:

##### 	基本知识：

​		-`\{{\}}`---文本或数据显示的地方，里面只运行js代码，纯js代码也可以运行。

 		-标签有的指令： 

​				 -v-html---可以显示数据中带有标签的，标签内的部分部分。标签内按照样式显示。

​				 -v-text---把标签也输出，也没有相应的标签效果。

​		-v-show=”定义的值“ 值是布尔值 控制一个值的隐藏或显示  。相当于是将相应的display：none。如果需要频繁的切换，使用v-show

​		- v-if=”定义的值“ 值时boolean 节点的动态创建和删除。相当于是dom中的appendChild（） removeChild（）如果运行时条件很少变换，则使用v-if

​				-动态切换class的方式，三目写法，对象写法，数组写法（可以任意的切换）	

​				-v-bind=‘值’ 动态切换class （isActive？‘red’：‘yellow’）buttom中写@click=‘handleClick（）’ 然后在methods中写入click的方法。 **bind和click要结合使用**

 	 	-列表渲染：v-for 循环渲染数据。有index，key值

   			 -key:必要值。跟踪每个节点的身份，重用和重新排序现有的元素。key="data.id" //理想的key值，每一项都有id

​				-v-for，在数组中结合computed/methods计算来控制数组数据的变换。

​		-传值：使用prop将数据传输到组件中。（尝试自己写组件TODOlist）

​        数组更新检测：

​            1：使用一下方法操作数组，可以检测变动。

​                push，pop，shift，unshift，splice，sort，reverse

​            2：新数组替换老数组。

​                filter，concat，slice，map

​	-在组件中：data必须是一个函数，template优先级比较高，数据驱动视图





​    事件处理：

​        1：@click=”事件“（函数写不写括号，主要是要看需不需要传输数据。）在methods中写响应事件所对应的方法（函数），然后当监听到事件发生改变时就可以运行了。

​        2：click会产生冒泡现象，所以原生使用stoPropogation来阻止。vue中有.stop的事件修饰符，用来阻止冒泡。.prevent阻止事件跳转。.self事件只有自己才可以触发。.once只能执行一次的事件修饰符。   

​        3：按键修饰符： @keyup.enter (后者是我们想要设置的特殊键值)

​		4：在内联语句处理器中访问原始的dom节点，可以用特殊变量$event传入方法内。

​		5：事件修饰符：事件+.事件修饰符 能更好的处理事件的细节。.stop-阻阻止事件冒泡.prevent-拦截默认事件.capture-事件变为捕获.self-只在自己范围内触发.once-只触发一次.passive-不拦截默认事件。（要注意修饰符的顺序）

​		6：按键修饰符：.enter.tab.delete.esc.space.up.down.left.right(就是添加一些特殊的键值)

​		7:系统修饰符：.ctrl.alt.shift.meta-对应着mac上的cmd键。.exact--可以和前面的串联，表示只有某个特殊按键的时候才会触发。

​		8：鼠标修饰符：.left.right.middle



​	双向绑定：v-model，通常和表单一起使用。

​		-vue中的v-model和v-bind：

​    		-v-model是双向绑定,即表单可以拿到vue中的数据,表单中的数据也可以传到vue中。

​    		-v-bind:value 只能是表单拿到vue的数据,vue无法拿到表单的数据。

​		-修饰符：.lazy--可以控制v-model绑定的数据在change事件之后同步.number--可以直接将输入的值转换成数值类型(通用).trim--可以自动过滤收尾的空白字符。



​	-动态组件：v-bind:is=“属性”(这个属性包括：已注册组件的名字/一个组件的选项对象)



##### 组件注册：

-组件名：推荐使用糖葫芦写法，驼峰也是可以的。

-全局注册：Vue.cmponent()注册的组件可以使用在new Vue()创建出来的根实例中。 

-局部注册：var 组件1={}来定义组件，然后在new Vue实例中可以通过components:{'组件名'：组件1}来定义。*局部注册的组件在其子组件中不可用。想要使用的话，只能在模块系统中局部注册->import 组件 from ‘vue文件中’ export default{ components:{ 组件1，组件2 } }

​	-？？？在想要只使用基础组件中的一部分时，可以使用require.context只全局注册这些非常通用的基础组件。可以在应用的入口文件（src/main.js）中全局导入基础组件。

##### prop：

-命名：使用驼峰写法

-类型：props:[‘字符串1’，‘字符串2’...] 但最好是是能够以对象的形式列出prop(值：类型)

-传值：任何一个类型的值都可以传递给一个prop，

-单向数据流：父级prop的更新会向下流到子组件中，

-使用：在父组件中通过v-bind定义一个值。在子组件的vue实例中定义该属性，并把值设为目标属性的数字即可。这样子组件就能接受到父组件中的属性值向下流下来的数据。

-验证：为了验证prop中属性传来的值的类型是否正确。验证失败时会产生一个控制台的警告。

-非prop的attribute？？

##### $emit：

-事件名：推荐是用糖葫芦写法。

-作用：子组件使用它来触发父组件的自定义事件。$emit(event,arg)

-使用：父组件 v-bind=“属性” 子组件 prop来接受父组件传来的数据。子组件监听了一个事件来来触发父组件中的事件。(子组件的事件触发，来接连触发父组件的事件。)

##### <slot>：

-就是给组件中挖了一个坑，只要在组件的模板中写入了<slot></slot>,那么组件在渲染的时候，写插槽的地方将会被替换为html中组件内写的内容。如果没有，那么中间的内容都会被抛弃。(就像是一个立体的空心积木)

-是子组件中提供给父组件使用的一个占位符，父组件可以向里面填充任何的内容。

-具名插槽：有名字的插槽，因为一个子组件中可以加入很多个插槽，为了能区分它们，就有了它。子-<slot name='header'> 父-<template v-slot:header> 使用v-slot来连接子中插槽。

-默认插槽：没有命名的就是默认插槽，但是前提是子中有<slot> 父中有传值

-作用域插槽：带参数的插槽，子组件提供给父组件一个仅用于插槽中的参数，父组件就可以通过不同的方式展示和填充内容。？？

-过滤器：为页面数据添油加醋的功能。

​	-局部：1：在vue实例中，添加一个filters:{ 方法，用来修改或筛选后端传过来的数据  }来声明过滤器2：使用`{{ 数据\|过滤器的名字}}  过滤`器就是一个函数。

​	-全局：vue.filter('过滤器名字'，函数逻辑)

-watch：监听的是单个属性，基本类型普通监听，复杂类型 deep监听。监听操作的是数据，而计算操作的是函数。

-methods:直接修改的数据属性





##### 渲染函数：



##### 单文件组件：

-SPA：单页Web应用。特点：在前后端分离的基础上加了一层前端路由

-扩展名：.vue。

-其中，css可以使用预处理器来构建。



前面学到的是vue2，好上手，但是实际应用中要用vue全家桶(vue全家桶：vue-cli，vue-router，vue-resource，vuex) vue-cli:脚手架，相当于是启动了一个请求服务器，把环境搭建好了，只要开发就行。

脚手架的使用：

​    1：先安装一个全局webpack。npm install webpack -g。再安装一个全局的vue-cli。 npm install -g vue-cli.

​    2:cd 进一个要放项目的文件夹 直接创建一个.vue文件。vue create + 项目名。(vue 3.X以上使用，2.x就用npm install webpack + 项目名)

​    3：安装相应的依赖。npm install

​    4:起项目。npm run start （也可以显式的指定入口文件。不太会）



vue引入公共样式的三种方式：

​    1：入口main.js中引入。  import  from  

​    2：在index.html中引入。

​    3：直接在app.vue中引用，但在index.html的head上空出一个<style>



vue组件父子传值的4种方法:props，ref,emit,模板传递通信slot

​    -props：

​        静态传值就是直接通过props来传递。

​        动态传值是通过v-bind来绑定一个要传递值的key，然后后面跟要传递的内容，不过这个内容是可以改变的

​	-slot：父组件在使用子组件的同时并向其中传值。



·vue里的ref（$ref）:

​    1、ref 加在普通的元素上，用this.ref.name 获取到的是dom元素

　　 2、ref 加在子组件上，用this.ref.name 获取到的是组件实例，可以使用组件的所有方法。

　  3、如何利用 v-for 和 ref 获取一组数组或者dom 节点



·prop 着重于数据的传递，它并不能调用子组件里的属性和方法。像创建文章组件时，自定义标题和内容这样的使用场景，最适合使用prop。

·$ref 着重于索引，主要用来调用子组件里的属性和方法，其实并不擅长数据传递。而且ref用在dom元素的时候，能使到选择器的作用，这个功能比作为索引更常有用到。



ref  $refs:

​    ·ref指定了某个dom节点。（相当于是一个字符串型的索引值）

​    ·refs是所有ref的集合。

​    ·ref和v-for一起使用时，获取的引用会是一个数组，



--html中 ref="profile"

--组件中  child = perent.$refs.profile(child是perent中所有dom节点的集合，标识就是profile)



表单验证：validate()

​    p=this.$refs.form.validate()  submit过来的从上面传来的表单值，是否有效，p.then.

##### vue-router：

-**核心：**改变url，但是页面不进行整体的刷新。结合vue.js来创建单页应用。   可以通过组合组件来组成应用程序，当把路由加入后，只需要将组件映射到路由，然后告诉路由在哪里渲染。

-**路由规则：**hash和history

​	-hash：#=锚点，本质是改变window.location的href属性。可以直接赋值location.hash改变href，但页面不刷新。

​	-history：可以改变url而不刷新页面。(比较新，IE9之前不能使用，所以hash更加通用一些)

​		-history.pushState()：类似栈，有进有出

​		-history.replaceState()：替换url，没有退回(常用的)

​		-history.back()

​		-history.forward()

​		-history.go(num)

-**路由分类：**

​	-动态路由：path:'/user/:id' .以冒号开头，只要前缀相同就都能映射到相同的路由上去。

​	-嵌套路由：有同一个父路由的路由。在普通路由配置的时候加入一个children：[{其他路由}]

​	-命名路由：给路由加一个name，在使用`router-link :to="{ name：‘xx’，params：{xx}}" name`是前半段，params是后半段。跳转的路径是/xx/xx.

-**路由视图：**<router-view></router-view> --必须有，相当于是在页面中给路由站了一个位置。

-props：在路由中加入props参数，可以将组件和路由解耦，这样使的组件更易重用和测试。**设置：**props：true 。这样就会将route.params设置为组件属性（???）---传参这里有很大的问题。

-**步骤：**

1：定义路由或者从别处引入，<script src="./vue-router.js"></script>。

2:准备路由所需要的组件。(能够跳转的块)。

3：创建路由对象，在对象中配置路由规则 var routes=new VueRouter({ path:'/foo',component:Foo })。（这两值必备，name可有可无）

4：在vue中注入路由。vue实例中，加入一个router。

5：通过<router-view></router-view>挖坑，路径匹配到的组件都会渲染到这来。

6：路由通过<router-link to="相应路由的path">跳转，这个被渲染后会变成a标签，值的前面会变成一个#，从而变成锚点。(链接的一种，就是在<a name="xxx" href="#hello">这就是在特定的xxx的地方设置了一个锚点。)

-**实际操作：**

​	1：在组件目录下写spa，然后在router目录下使用import引入之前写的spa(使用相对路径(相对路径：./文件名表示在当前目录下。))

​	2：在router目录中的index.js，的下面写入相应的路由，按照给定的模板写。引入时要注意new router的地址。import .. from 'new router的地方'(给的模板中设置的name是用在嵌套路由上的。)

​	3：在main.js中import相应的router

​	4：在app.vue中加入<router-link>来定义页面中点击触发部分(定义当点击后去到的地方)<router-view>来在页面中显示。

​	5：重定向-就是在路由中一定要加一个路由，指向有的页面（用户输入了不存在的路由，跳转到有用的页面去）两种写法：1：path:'*',redirect:'/组件' 2：path:'\*',redirect:{name:'组件'}。

-**路由守卫：** 就是在路由的基础上添加了钩子函数	

​	-全局前置守卫：router.beforeEach((to,from,next)=>{})  to=即将进入的目标路由对象-到哪去。from=当前要离开的路由-从哪来。next=function，一定要调用这里的方法，来resolve这个钩子。next函数中的参数，会影响执行效果。【无参->进行下一个钩子，如果全都执行完了，那么导航的状态就是confirmed。false->中断当前的导航。在正在改变url的过程中，那么url地址会重置到from路由对应的地址。'/'->跳转到不同的地址。中断正在跳转的地址，然后去一个新的地址。(可以传递任意函数？？？)。error->导航过程会被终止，并且错误会传去router.onError()注册过的回调中去。】

​	-全局解析守卫：router.beforeResolve()=和上面类似。区别：在导航被确认之前，同时在all component内守卫，和异步路由组件被解析之后，解析守卫被调用。

​	-全局后置钩子：router.afterEach((to,from)=>{})。没有next，不会改变导航本身。

-**导航解析流程：** (导航：路由正在跳转的过程)

触发导航 -> 在失活的组件里调用 `beforeRouteLeave` 守卫。(失活的组件就是要被离开的组件)->调用全局的 `beforeEach` 守卫。(在导航前)->在重用的组件里调用 `beforeRouteUpdate`(路由改变，组件被复用时调用)->在路由配置里调用 `beforeEnter`->解析异步路由组件->在被激活的组件里调用 `beforeRouteEnter`->调用全局的 `beforeResolve`->导航被确认->调用全局的 `afterEach` 钩子->触发 DOM 更新->调用 `beforeRouteEnter` 守卫中传给 `next` 的回调函数，创建好的组件实例会作为回调函数的参数传入

-元信息：

-**过渡动效：** 加入一个<transition></transition> 来实现切换路由时中间的过渡动画。

-**数据获取：** 两种，导航完成**前**-在路由进入的守卫中获取数据，获取数据之后再进行导航/**后**-先导航，结束后在组件的生命周期钩子中获取数据。

-**滚动行为：** 控制页面来回回滚后，前的滚动条进度保持的位置。**使用：** 给router实例中，加入一个scrollBehavior(to, from, savePosition)方法。

##### 路由参数：

-router传递参数：使用上面的那个router-link

-接受参数：

​	-组件接收：在html中获取路由参数, 通过$route.params.参数名

`var productType = Vue.component('productType',{`
    `//在html中获取路由参数, 通过$route.params.参数名`
    `template:'<div>这里显示商品编号{{$route.params.id}}</div>',`
`})`

​	-js接收：在js中获取路由参数, 通过this.$route.params.参数名

`var productType = Vue.component('productType',{`
    `//在html中获取路由参数, 通过$route.params.参数名`
    `template:'<div>这里显示商品编号{{$route.params.id}}</div>',`
    `//模板编译完成之后调用`
    `mounted() {`
        `//在js中获取路由参数, 通过this.$route.params.参数名`
        `console.log(this.$route.params.id)`
    `},`
`})`

-this.$route.query和this.$route.params的区别：

​	传参数时，query:{path: item.id} url中会带有参数 params:{name: item.id} url中没有参数显示

-响应路由的参数变化：

##### vuex：

-专门为vue.js开发的状态管理模式，集中管理所有组件的状态。

state--大树的树干--共用的数据，不同的组件就像树的分叉，会使用树的一部分数据，但是会根据自己做出一些调整。这个调整可以使用mutation改变，(过程是同步的？？？---就是逻辑是同步改变的)异步逻辑都封装到action里面。

-vuex部分文件：api-里面会放一些抽出来的api请求，与后台交互的请求响应代码。？？？   Component-放一些单页面组件，store-index.js=组装模块并导出store的地方，actions.js=根级别的action，mutation.js=跟级别的mutation。modules-中存放着各种模块（这种模块中放的是什么）

-一个模块中，要创建state，mutation，action，getter

-**state：**在vue实例中，可以通过this.$store.state.data(可换，数据名，来访问到store中的数据)。当一个组件需要获取多个状态时(数据???)将这些状态都声明在计算中会冗余，这时候，可以使用mapState辅助函数---生成计算数据。（就是在computed中写了一个mapState函数，将上面的参数简化。）

-**getter：** state的计算属性，就像vue中的computed一样，返回值也会根据他的依赖被缓存起来，依赖值改变才会改变。getter会暴露一个  store.getter的对象，(数据在getter中被计算，我们可以使用store.getter来直接调用这些数据)在getter中也能接受其他的getter的参数。

-**actions：** state中出来的数据，action要来取数据，然后action中取完的数据（使用commit，其中有两个参数，事件，(???回调函数吗，是什么)）才能再使用mutation来修改里面的值。action 提交的是mutation，而不是直接改变状态。有它的原因就是为了可以在成功和失败两个状态之间横跳。可以使用promise 也可以使用async/await

-**mutation：** 改变store中的状态，(就像是在原有的树枝上长出一截新的树枝。)有事件和回调函数。(我现在的理解就是他就像java里面的那个函数重写一样，在原有的基础上给原来的增加一些方法)

-new store-创建实例，其中必备state来存放一个大的共享数据，

state写数据->要改变数据状态->action提交mutation->mutation直接改变数据。







Q:1：v-model绑定，循环渲染的时候value怎么设置。

2：ref，prop的具体区别，实际使用的时候呢

3:fx-cascader中的数据怎么传

4:为什么有时候按钮不触发事件