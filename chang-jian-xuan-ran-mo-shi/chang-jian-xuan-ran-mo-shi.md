# 常见渲染模式

常见渲染模式分为浏览器端渲染(CSR)和服务器端渲染(SSR)。

## 浏览器端渲染

浏览器端渲染，CSR(Client Side Render),页面上的内容是我们加载的js文件渲染出来的，js文件运行在浏览器上面，服务端只返回一个html模板。

<figure><img src="../.gitbook/assets/浏览器端渲染.jpg" alt=""><figcaption></figcaption></figure>

## 服务器端渲染

服务器端渲染,SSR(Server Side Render),页面上的内容是通过服务端渲染生成的，浏览器直接显示服务端返回的html就可以了。在遇到首页白屏的情况下，服务器端渲染用时会少些。

默认情况下，框架可以在浏览器中输出组件，进行生成 DOM 和操作 DOM。然而也可以将同一个组件渲染为服务器端的 HTML 字符串，将它们直接发送到浏览器，最后将这些静态标记"激活"为客户端上完全可交互的应用程序。

服务器渲染的应用程序也可以被认为是"同构"或"通用"，因为应用程序的大部分代码都可以在服务器和客户端上运行。

<figure><img src="../.gitbook/assets/服务器端渲染.jpg" alt=""><figcaption></figcaption></figure>

## 不同渲染方式在浏览器解析情况

浏览器中输入URL开始，流程如下：

1.解析URL

2.浏览器本地缓存

3.DNS解析

4.建立TCP/IP连接

5.发送HTTP请求

6.服务器处理请求并返回HTTP报文

7.浏览器根据深度遍历的方式把html节点遍历构建DOM树

8.遇到CSS外链，异步加载解析CSS，构建CSS规则树

9.遇到script标签，如果是普通JS标签则同步加载并执行，阻塞页面渲染，如果标签上有defer / async属性则异步加载JS资源,如果是延时加载则，会根据情况按需加载。

10.将dom树和CSS DOM树构造成render树

11.渲染render树
