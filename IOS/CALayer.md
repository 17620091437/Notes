### CALayer

UILayer是UIView的属性，是UIView能显示的原因，是一个图层

可以修改UIVIew的外观样式

#### 常用属性

![img](https://upload-images.jianshu.io/upload_images/2498154-59ed37a8e2b3545c.png)



---

CALayer是定义在QuartzCore框架中  （跨平台）

CGImageRef、CGColorRef 定义在CoreGraphics框架中   （跨平台）

UIColor、UIImage定义在UIKit框架中  （IOS）

UIView可以处理事件



position设置CALayer在父层中的位置，以父层左上角为原点（0,0）

anchorPoint锚点，以自己的左上角作为原点（0,0）,x和y取值范围0~1，默认值为（0.5，0.5）



---

####隐式动画

非根层CALayer修改属性会有隐式动画   动画事物

[CATransaction setDisableAction：]启动或关闭动画

[CATransaction setDisableDuration：]时长