### xib和storyboard对比

相同

都是用来描述然间界面，用Interface Builder工具编辑，本质都是转换成代码去创建控件

不同

xib轻量的，描述局部界面

storyboard重量级的，描述多个界面，和跳转关系



加载方法

[[[NSBundle mainBundle]loadNibNamed: owner: options:]firstObject]



xib添加数据 ：在xib中修改类名，新建一个类，属性对应子控件，然后连线，就能访问子控件，暴露接口设置数据。

Xib在代码添加子控件 （view的子控件）：在类中新增一个属性用来保存新增的子控件，因为在xib中加载控件会调用initWithCoder方法，所以在此方法中生成并添加子控件，然后在layoutSubviews方法中布局子控件 

xib在代码中添加 View的子控件的子控件 ：参考上面，但是在initWithCoder方法中，view的子控件并没有被唤醒，所以要在awakeFromNib方法中创建。



xib的view被加载，不会调用init和 initWithFrame
