#### dom：

-用来实现页面的动态交互效果。html的每一个标签都能成为dom的一个节点。

​	-节点分类：-文档~：文档本身。-元素~：所有的html元素。-属性~：html元素内的属性。-文本~：元素内的文本。-注释~：html中的注释。

-获取元素：

`document.getElementById('xxx') //通过Id来获取对象，后面的都是数组	document.getElementsByTagName('div')[0] //通过标签名获取(获取第1个div标签) document.getElementsClassName('red')[0] //获取第1个class='red'的元素`

（上面方法在兼容IE的情况下再使用）



`document.querySelector('') //获取元素(第一个遇到的) 	document.querySelectorAll('div') //获取所有含有div的元素 		document.querySelectorAll('div')[0] //获取第一个div标签`

（常用的）



-获取特定元素：

`document.documentElement //获取html元素`

`document.head //获取head元素`

 `document.body //获取body元素`

 `window //获取窗口，可通过`

`window.onclick 对窗口进行监听` 

`document.all //获取所有的标签`

-biao'd



-新增节点：

`document.createElement()//标签节点`

`document.createTextNode()//文本节点`

`div1.appendChild(text1)      div1.innerText = '你好'    div1.textContent = '你好'//将文本节点插入到元素中去。`

`document.body.appendChild(div1)     div1.appendChild(text1)//将在页面中的元素插到页面中。`

`let text2 = text1.cloneNode.call(text1,true)//true-深拷贝，false-浅拷贝。`//拷贝的原因是节点只能被添加一次，不能重复使用，如果想要重复使用就要拷贝。

-删除节点：

div.parentNode.removeChild(div1) //从树种删除节点

-改属性：

div.className //修改class

div.style//修改style

div.dataset//?



#### Bom:

-js可以处理的事件有：鼠标事件（blur-元素失焦，focus-元素聚焦，mouseover-鼠标移上，mouseout-鼠标移开，click-点击）键盘事件（keyup-按键松开，keydown-按键按下）HTML事件（load-加载）。在前面加上了on-就变为了一个事件处理程序。

-bom对象方法：alert()-弹出警示,confirm()-确认框，返回boolean值，prompt()-输入框，返回提示框中的值，方法可以调用系统对话框向用户显示消息。

-bom对象：

​	-history：历史对象，包含用户访问过的URL。

​		-back():加载前一个url

​		-forward：加载下一个url

​		-go(num)：加载url表中相应的位置，-1-上一个url

​	-location：与当前窗口加载的文档相关的信息。 href属性-设置或返回完整的url

​		-reload：重新加载当前文档

​		-replace：用新的文档代替当前文档

​	-document：