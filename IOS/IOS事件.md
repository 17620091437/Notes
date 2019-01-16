### IOS事件

- 触摸事件
- 加速计事件
- 远程控制事件

---

#### UIResponder

只有继承UIResponder才能接受处理事件

![image-20190115165846286](/Users/efun/Documents/Notes/IOS/assets/image-20190115165846286.png)

---



#### UITouch

一个触控点对应一个UITouch对象

保存触摸位置、时间、阶段

手指移动时系统会更新同一个UITouch对象



#### UIEvent

每产生一个事件就会产生一个UIEvent对象

记录产生事件的时刻和类型



---

#### 事件的产生和传递(类似事件捕抓)

1. 发生触摸事件后，把事件加入UIApplication管理的事件队列中

2. 取出首事件，分发给主窗口(keyWindow)

3. 在视图层次结构中找到一个最合适的视图来处理触摸事件

4. 找到合适的视图控件后，调用视图控件的touches方法处理



不能接受触摸事件的三种情况

userInteractionEnabled = NO

Hidden =YES

Alpha  = 0~0.01



当控件不能接受触摸事件，传递就会断



传递过程中调用hitTest: withEvent

内部调用pointInside: withEvent 判断触摸点在不在当前view



---

####事件响应链

事件响应方法默认往上传递