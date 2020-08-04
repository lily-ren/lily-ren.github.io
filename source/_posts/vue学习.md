## vue学习:

#### 	1:基本知识：

​		-{{}}--文本或数据显示的地方，里面只运行js代码，纯js代码也可以运行。

 		-标签有的指令： 

​				 >v-html--可以显示数据中带有标签的，标签内的部分部分。标签内按照样式显示。

​				 >v-text--把标签也输出，也没有相应的标签效果。

​		-v-show=”定义的值“ 值是布尔值 控制一个值的隐藏或显示  。

​		- v-if=”定义的值“ 值时boolean 节点的动态创建和删除。

​				>动态切换class的方式，三目写法，对象写法，数组写法（可以任意的切换）	

​				>v-bind=‘值’ 动态切换class （isActive？‘red’：‘yellow’）buttom中写@click=‘handleClick（）’ 然后在methods中写入click的方法。 **bind和click要结合使用**

 	 	-列表渲染：v-for 循环渲染数据。有index，key值

   			 >key:必要值。跟踪每个节点的身份，重用和重新排序现有的元素。key="data.id" //理想的key值，每一项都有id

​				>v-for，在数组中结合computed/methods计算来控制数组数据的变换。

​		-传值：使用prop将数据传输到组件中。（尝试自己写组件TODOlist）

​        数组更新检测：

​            1：使用一下方法操作数组，可以检测变动。

​                push，pop，shift，unshift，splice，sort，reverse

​            2：新数组替换老数组。

​                filter，concat，slice，map

​	-在组件中：data必须是一个函数，





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

##### 渲染函数：



##### 单文件组件：

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

-使用：结合vue.js来创建单页应用。   可以通过组合组件来组成应用程序，当把路由加入后，只需要将组件映射到路由，然后告诉路由在哪里渲染。

-步骤：

1：定义路由或者从别处引入，<script src="./vue-router.js"></script>。

2:准备路由所需要的组件。(能够跳转的块)。

3：创建路由对象，在对象中配置路由规则 var routes=new VueRouter({ path:'/foo',component:Foo })。(这三个值是必备的)

4：在vue中注入路由。vue实例中，加入一个router。

5：通过<router-view></router-view>挖坑，路径匹配到的组件都会渲染到这个组件来。

6：路由通过<router-link to="相应路由的path">跳转，这个被渲染后会变成a标签，值的前面会变成一个#，从而变成锚点。(链接的一种，就是在<a name="xxx" href="#hello">这就是在特定的xxx的地方设置了一个锚点。)

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

-响应路由的参数变化：

##### vuex：

-专门为vue.js开发的状态管理模式，集中管理所有组件的状态







Q:1：v-model绑定，循环渲染的时候value怎么设置。

2：ref，prop的具体区别，实际使用的时候呢

3:fx-cascader中的数据怎么传

4:为什么有时候按钮不触发事件