---
title: curl
tag: 杂项
---
-curl-command line url viewer。一个命令行工具。发出网络请求，然后得到和提取数据。

-使用：

​	-curl + url =直接显示网页源码

​	-curl -o [文件名] +url = 保存网页源码

​	-curl -L +url = 自动跳转页面

​	-curl -i + url = 显示response的头部消息，连同代码一起

​	-curl -v + url = 显示一次http通信的过程，请求和接收都能看见

​	-curl --trace(--trace-ascii) [文件名] url = 更详细的通信过程

​	-curl url/表单内容 = 使用GET方法发送表单

​	-curl -X POST(--data-urlencode) --data + "数据" + url = 使用POST方法发送，注意数据要和url分开。 (可以让curl帮忙编码未编码的表单)(curl默认的http动词是get，所有要使用别的时，要在前面加上 -X)

​	-curl --form upload=@本地文件名 --form press=OK [url] = 从文件上传表单

<form method="POST" enctype='multipart/form-data' action="upload.cgi">
　　　　<input type=file name=upload>
　　　　<input type=submit name=press value="OK">
</form>

​	-curl --referer + url = 在response头部信息中，提供一个Referer字段，表示是从哪里跳转过来的。

​	-curl --user-agent "[user agent]" [url]  = 表示客户端的设备信息。服务器会根据不同的设备，返回不同格式的网页。

​	-curl --cookie "name=xxx" url = 可以发送cookie

​	-curl --header "头部内容" + url = 在请求头中自行增加一个头信息。

​	-curl --user name:password + url = 需要进行http认证的时候。



详细参考表：http://www.ruanyifeng.com/blog/2019/09/curl-reference.html