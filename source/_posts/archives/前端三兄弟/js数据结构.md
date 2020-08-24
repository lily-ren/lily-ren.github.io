---
title: JS数据结构
tag: 前端三兄弟
---
## 数组：

##### -方法：

-数组迭代：

​	-every(过滤器函数):迭代数组中的每一个函数，直到出现false。

​	-some:同every相反，直到返回true。

​	-forEach():和使用for相同。	

​	-map():创建了新数组，每一个都迭代

​	-filter():创建新数组，只存放返回值是true的那个。

-数组缩小：

​	-reduce(function(preV,curV,idx,arr)):内部函数会返回一个叠加到累加器的值。常用于数组所有元素求和。

​	-reduceRight():从最后一项到第一项

-数组转换：

​	-array.toString():

​	-array.valueOf:将数组作为字符串返回。

​	-array.join(不同连接符):将数组元素连接成串。

-数组的栈方法:(用来操作队列尾部)

​	-array.push():移入队尾

​	-array.pop():删除队尾

-数组的队列方法:(用来操作数组的头部，来模拟队列)

​	-array.push():推入队尾

​	-array.shift():将数组第一个值移除。

​	-array.unshift():将数组第一个值加入。可以用来模拟反向队列。

-数组重排序方法：

​	-array.reverse():只能翻转

​	-array.sort(比较函数):通常结合比较函数一起使用。

-数组操作方法：

​	-array.concat(array)--拼接，创建一个新数组

​	-array.slice(start,end):分割，返回分割后的数组，不会影响原数组。

​	-array.splice(index,number)/(start,end,添加的元素):可以删除，插入，替换。是功能最强大的数组方法。

-数组位置方法：

​	-array.indexOf(index,查找起点):输出与搜索值相同的第一个值的索引。

​	-array.lastIndexOf(同上)：

##### -Data类型：

`Var now = new Data();` 在不传参的情况下，直接获取当前时间（系统还是本地？）

-Data.parse(data string)：会将字符串转换成日期。但不同浏览器的解析不同。

-Data.now():返回当前时间的毫秒数。在不支持使用的浏览器中，可以使用+new 把对象转换成字符串。

-toUTCString():实现特定于实现的格式显示时分秒 ？？？

##### -RegExp类型：

-用来支持正则表达式（就是为了查找使用的），`var expression = / pattern / flags` 

pattern-正则表达式。flags-标识，有g(全局模式，模式被使用于所有字符串),i（不区分大小写）,m（多行模式）

-实例属性：regexp.global/ignoreCase/multiline-布尔，看是否设置了g，i，m .lastIndex-整数，开始搜索下一个匹配项的字符位置,source-正则的字符串表达式。

​	