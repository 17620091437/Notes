###Quartz 2D

二维绘图引擎(类似canvas)

- 裁剪图片
- 涂鸦画板
- 手势解锁
- 报表图形

自定义UI控件

---

####图形上下文

CGContextRef类型 

保存绘图信息、绘图状态

决定输出的目标

![image-20190116115417997](/Users/efun/Documents/Notes/IOS/assets/image-20190116115417997.png)

**图形上下文类型**

- Bitmap 图片

- PDF

- Window

- Layer

- Printer



---

#### 自定义view

1. 首先要有图形上下文，保存绘图信息，决定绘制到什么地方
2. 图形上下文跟UIView相关联，才能将内容绘制在view上面 

**实现**

- 新建一个类继承UIView
- 实现- (void) drawRect: 方法，默认生成跟UIView关联的Layer上下文
- 取得图形上下文，绘制图形内容，将上下文的内容渲染显示到view上



-(void) drawRect: rect

在控制器的 viewWillAppear 后和viewDidAppear 之间调用，rect参数为view的bounds

1. 获取上下文
2. 绘制路径
3. 把绘图内容保存到上下文中
4. 把上下文内容显示到view中，渲染到view的layer