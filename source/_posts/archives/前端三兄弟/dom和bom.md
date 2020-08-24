---
title: DOM和BOM
tag: 前端三兄弟
---
#### dom：HTML和XML的应用程序接口

-用来实现页面的动态交互效果。html的每一个标签都能成为dom的一个节点。

​	-节点分类：-文档~：文档本身。-元素~：所有的html元素。-属性~：html元素内的属性。-文本~：元素内的文本。-注释~：html中的注释。

-获取元素：

`document.getElementById('xxx') //通过Id来获取对象，后面的都是数组	document.getElementsByTagName('div')[0] //通过标签名获取(获取第1个div标签) document.getElementsClassName('red')[0] //获取第1个class='red'的元素`

（上面方法在兼容IE的情况下再使用）



`document.querySelector('') //获取元素(第一个遇到的) 	document.querySelectorAll('div') //获取所有含有div的元素 		document.querySelectorAll('div')[0] //获取第一个div标签`

（常用的）

-新增节点：

`document.createElement()//标签节点`

`document.createTextNode()//文本节点`

`div1.appendChild(text1)      div1.innerText = '你好'    div1.textContent = '你好'//将文本节点插入到元素中去。`

`document.body.appendChild(div1)     div1.appendChild(text1)//将在页面中的元素插到页面中。`

`let text2 = text1.cloneNode.call(text1,true)//true-深拷贝，false-浅拷贝。`//拷贝的原因是节点只能被添加一次，不能重复使用，如果想要重复使用就要拷贝。

-获取属性：dom对象.属性=“xxx”

-删除节点：

div.parentNode.removeChild(div1) //从树种删除节点

-改属性：

div.className //修改class

div.style//修改style

div.dataset//?

-修改节点：

​	-appendChild()//指定节点的最后一个节点列表后添加一个新的子节点

​	-insertBefore()//将一个给定节点插入到一个给定元素节点的给定子节点的前面

​	-removeChild()//从一个给定元素中删除子节点

​	-replaceChild()//把一个给定父元素里的一个子节点替换为另外一个节点

-访问节点：

​	-`document.documentElement //获取html元素`

​	-`document.head //获取head元素`

​	-`document.body //获取body元素`

 	-`window //获取窗口，可通过`

​	-`window.onclick 对窗口进行监听` 

​	-`document.all //获取所有的标签`

-node节点的特性和方法：

​	-firstChild //获取第一个子节点

​	-lastChild//获取最后一个子节点

​	-parentNode//指向父节点

​	-ownerDocument//指向这个节点所属的文档

​	-childNodes//所有子节点列表

​	-hasChildNodes() //Boolean，当childNodes包含一个或多个节点时，返回真值

-dom事件：	

​	-冒泡事件：从内向外

​	-捕获事件：从外向内

​	-阻止冒泡：

​		-event.stopPropagation()    event.stopImmediatePropagtion()--阻止剩下的事件处理程序被执行

​		-preventDefault()--

​		-innerText--表示起始标签和结束标签之间的文本、innerHTML--表示元素的所有元素和文本的HTML代码、outerText--替换的是整个目标节点，返回的和innerText相同、outerHTML--同上

​	-事件监听函数：

​		-oDiv.onclick = function(){}//默认冒泡

​		-attachEvent() ，detachEvent()//在IE中使用？//都有两个参数--事件动作，回调函数。//在使用attachEvent()方法中，事件处理程序会在全局作用域中运行。

​		-addEventListener()和removeEventListener()//用来分配和移除事件处理函数//三个参数：事件名称，要分配的函数，事件阶段是在什么阶段。

​		-addHandler()，removeHandler()//跨浏览器的事件处理程序//addHandler()方法属于一个叫EventUntil()的对象，这两个方法均接受三个相同的参数，要操作的元素，事件名称和回调函数。



-事件类型：(在前面加上了on-就变为了一个事件处理程序)

​	-鼠标~：click-点击、dbclick-双击、mousedown-鼠标按下、mouseup-鼠标抬起、mouseover-鼠标移上、mouseout-鼠标移开、mousemove-鼠标移动

​	-键盘~：keydown-按键按下的过程、keypress-键被按下、keyup-按键松开

​	-HTML~：load-加载、abort-中途停止ajax请求、select-添加/触发select事件、change-添加/触发 change 事件、submit-添加/触发 submit 事件、 resize-添加/触发 resize 事件、scroll-添加/触发scroll 事件、focus-元素聚焦、blur-元素失焦









​	

#### Bom:用于处理浏览器窗口和框架。

-就是对浏览器的一些window窗口的操作的一些控制。

-bom对象方法：alert()-弹出警示,confirm()-确认框，返回boolean值，prompt()-输入框，返回提示框中的值，方法可以调用系统对话框向用户显示消息。

-bom对象：

​	-navigator：导航器对象，控制一些浏览器信息

​		-appCodeName：返回浏览器的代码名

​		-appName：浏览器名称	

​		-appVersion：浏览器的平台和版本信息

​		-cookieEnabled：指明浏览器中是否启用cookie的布尔值

​		-platform：运行浏览器的操作系统平台

​		-userAgent：返回由客户机发送服务的user-agent头部的值

​	-screen：显示器对象

​		-availHeight：显示屏幕可用高度

​		-availWidth：显示屏幕可用宽度

​		-height：屏幕的像素高度

​		-width：屏幕的像素宽度

​		-colorDepth：屏幕颜色位数

​	-history：历史对象，包含用户访问过的URL。

​		-back():加载前一个url

​		-forward：加载下一个url

​		-go(num)：加载url表中相应的位置，-1-上一个url

​	-location：与当前窗口加载的文档相关的信息。

​		-属性

​			-hash：设置或返回从#开始的url

​			-search：从？开始的url

​			-host：主机名和当前的url的端口号

​			-hostname：主机名

​			-port：端口号

​			-pathname：路径

​			-protocol：当前url的协议

​			-href：设置或返回完整的url

​		-方法

​			-assign(url)：加载新文档

​			-reload：重新加载当前文档

​			-replace：用新的文档代替当前文档

​	-document：文档对象

​			-方法：

​				-open：打开新的，擦除旧的

​				-close：关闭文档输出流

​				-write：向当前文档追加写入文本

​				-writeIn：同上，但会换行

​	![img](https://p.ssl.qhimg.com/t016c684c2c50e6468a.gif)