### UIImageView

属性

- img  保存UIImage对象
- animationImages  动画图片数组
- animationDuration  动画时长
- animationRepeatCount  重复次数

方法

- startAnimating
- stopAnimating
- isAnimating



图片设置方式

1.imgView.image=[UIImage imageName:@""];

加载Assets.xcassets里面的图片：打包后变成Assets.car，拿不到路径，只能用imageName加载，不能用imageWithContentsOfFile加载。

指向资源的指针被销毁，资料还是保留在内存中

Assets.xcassets会缓存



2.imgView.image=[UIImage imageWithContentsOfFile:@""];

放在项目目录中的图片，可以拿到路径，通过[NSBundle mainBundle] pathForResource:@""ofType:@""获取路径

指向资源的指针被销毁，资源内存会被清除

