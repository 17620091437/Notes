###UIViewController

touchesBegan:NSSet withEvent:事件



#### 生命周期

loadView  控制器创建view时调用

1. 判断当前控制器是否storyboard加载的，如果是，就把storyboard中的控制器的view,设置为当前控制器的view
2. xib加载的跟stroyboard类似
3. 控制器如果代码创建的，就会创建空白view

![image-20190114173007850](/Users/efun/Documents/Notes/IOS/assets/image-20190114173007850.png)

