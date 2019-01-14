###UIApplication

- 应用程序的象征

- 是一个单例
- [UIApplication sharedApplication] 可以获取
- 程序启动后第一个创建对象

---



#### 常用属性

应用程序图标右上角提醒数字

联网指示器的可见性

状态栏状态（默认是控制器控制的，需要修改为app统一控制）

跳转打开网页，邮件，打电话。。。

---



#### 应用程序代理delegate

应用程序生命周期事件

系统事件

内存警告 

---



#### 应用程序启动原理

1.执行main函数

2.执行UIApplicationMain，创建UIApplication对象，设置代理

3.开启事件循环（主运行循环，死循环，保证应用程序不退出）

4.加载info.plist（判断info.plist有没有main(storyboard),有就加载main.storyboard）

5.应用程序启动完毕

