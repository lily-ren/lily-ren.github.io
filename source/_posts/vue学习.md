## vue学习:

#### 	1:基本常识：

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





​    事件处理：

​        1：@click=”函数“（函数写不写括号，主要是要看需不需要传输数据。）

​        2：click会产生冒泡现象，所以原生使用stoPropogation来阻止。vue中有.stop的事件修饰符，用来阻止冒泡。.prevent阻止事件跳转。.self事件只有自己才可以触发。.once只能执行一次的事件修饰符。   

​        3：按键修饰符： @keyup.enter (后者是我们想要设置的特殊键值)



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

​    ·props：

​        静态传值就是直接通过props来传递。

​        动态传值是通过v-bind来绑定一个要传递值的key，然后后面跟要传递的内容，不过这个内容是可以改变的



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



·vue中的v-model和v-bind：

​    ·v-model是双向绑定,即表单可以拿到vue中的数据,表单中的数据也可以传到vue中。

​    ·v-bind:value 只能是表单拿到vue的数据,vue无法拿到表单的数据





Q:1：v-model绑定，循环渲染的时候value怎么设置。

2：ref，prop的具体区别，实际使用的时候呢

3:fx-cascader中的数据怎么传

4:为什么有时候按钮不触发事件