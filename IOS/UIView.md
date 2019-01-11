### UIView

所有控件的父类。

- 每个控件都是一个容器，可以放子控件。
- 每一个控制器都有一个UIView，控制器不可见，UIView可见，控制器有一个UIView属性，控制器中管理的所有子控件都是该UIView控件的子控件.

属性

- superView 父控件
- subViews 子控件数组
- tag 控件ID，父控件可通过tag来找到对应的子控件
- Transform 形变属性
- frame 在父控件中位置和尺寸
- bounds 前两个是重新设置本地坐标系左上角的坐标，会影响子控件的位置，后两个是以控件中心作为原点设置宽高
- center 自己中心相对父控件做左上角的位置
- clipsToBounds  裁剪溢出
- contentMode  内容展示模式，内容的位置

方法

- addSubView 添加子控件
- removeFromView 将自己从父控件中移除
- viewWithTag 