# GET与POST区别

## 说明

#### GET方法
用get方式可传送简单数据，但大小一般限制在1KB下，数据追加到url中发送（http的header传送），也就是说，浏览器将各个表单字段元素及其数据按照URL参数的格式附加在请求行中的资源路径后面。
另外最重要的一点是，它会被客户端的浏览器缓存起来，那么，别人就可以从浏览器的历史记录中，读取到此客户的数据，比如帐号和密码等。因此，在某些情况下，get方法会带来严重的安全性问题。

#### Post方法
当使用POST方式时，提交的数据大小没有限制；浏览器把各表单字段元素及其数据作为HTTP消息的实体内容发送给Web服务器，而不是作为URL地址的参数进行传递，使用POST方式传递的数据量要比使用GET方式传送的数据量大的多。
一般线上服务器关于post也是会设置上限的。

总之，GET方式传送数据量小，处理效率高，安全性低，会被缓存，而POST反之。


## 安全、幂等、可缓存的
GET的语义是请求获取指定的资源。GET方法是安全、幂等、可缓存的（除非有 Cache-ControlHeader的约束）,GET方法的报文主体没有任何语义。

POST的语义是根据请求负荷（报文主体）对指定的资源做出处理，具体的处理方式视资源类型而不同。POST不安全，不幂等，（大部分实现）不可缓存。


## 提交方法时action页面后边带的参数列表会被忽视
`<form method="get" action="a.asp?b=b">`跟`<form method="get" action="a.asp">`是一样的，
也就是说，method为get时action页面后边带的参数列表会被忽视；

而`<form method="post" action="a.asp?b=b">`跟`<form method="post" action="a.asp">`是不一样的。
