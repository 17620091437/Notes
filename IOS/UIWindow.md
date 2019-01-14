### UIWindow

- UIWindow是一种特殊的UIVIew,app中至少有一个。
- ios程序启动后创建的第一个视图就是UIWindow,接着创建控制器的view,最后把控制器的view添加到UIWindow上，于是控制器的view就展示在屏幕上。
- 一个ios程序之所有能显示在屏幕上是因为有UIWindow

---



程序启动时，判断info.plist有无Main,有就加载Main.storyboard,然后先创建一个窗口（UIWindow），把Main.storyboard箭头指向的控制器设为窗口的根控制器，然后显示窗口（把根控制器的view添加到窗口）



如果不通过storyboard加载UIWindow，要在程序一启动是自行添加UIWindow

1.创建UIWindow,并赋值给app的window属性

2.创建控制器，并赋值给window的rootViewControl属性

3.显示控制器 

![image-20190114111639235](/Users/efun/Documents/Notes/IOS/assets/image-20190114111639235.png)

####makeKeyAndVisiable:

1. 设置应用程序主窗口（[UIApplication shareApplication].keyWindow属性可查看）
2. 让窗口显示，窗口默认是hidden
3. 把窗口的根控制器的view添加到窗口上阿萨德



状态栏和键盘也是窗口

窗口有层级