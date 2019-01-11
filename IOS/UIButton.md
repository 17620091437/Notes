### UIButton

5种状态

normal默认

highlighted高亮

disable不可用

selected选中



分状态设置文字、文字颜色、文字阴影、内容图片、背景图片



处理事件addTarget: action: forControlEvents:





无法在按钮外部修改内部子控件尺寸（UIImageView和UILabel）

#### 修改 UIImageView和UILabel位置

- 方式一

  新增类继承UIButton,重写titleRectForContentRect:  和imageRectForContentRect:   方法

- 方式二

  重写layoutSubviews，在layoutSubviews方法中改子控件的frame



####UIButton内边距

contentEdgeInsets属性  按钮内边距

imageEdgeInsets图片内边距

titleEdgeInsets标题内边距