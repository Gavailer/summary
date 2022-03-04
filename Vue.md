# Vue 

### 1.什么是MVVM、MVC？二者的区别是什么?

#### MVC

​	MVC 全名是 Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范

 * Model（模型）：是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据

 * View（视图）：是应用程序中处理数据显示的部分。通常视图是依据模型数据创建的

 * Controller（控制器）：是应用程序中处理用户交互的部分。通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据

   ![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/0e4d22e916014ee7abb10e4b350e5583~tplv-k3u1fbpfcp-watermark.awebp)

> 一句话描述就是 Controller 负责将 Model 的数据用 View 显示出来，换句话说就是在 Controller 里面把 Model 的数据赋值给 View。

#### MVVM

​	MVVM 新增了 VM 类

 * ViewModel 层：做了两件事达到了数据的**双向绑定** 一是将【模型】转化成【视图】，即将后端传递的数据转化成所看到的页面。实现的方式是：**数据绑定**。二是将【视图】转化成【模型】，即将所看到的页面转化成后端的数据。实现的方式是：**DOM 事件监听**。

   ![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/32c0545686454396a7e39b86b644fe73~tplv-k3u1fbpfcp-watermark.awebp)

