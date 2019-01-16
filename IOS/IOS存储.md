### IOS存储

- xml(plist)
- Preference(偏好设置)
- NSKeyedArchiver归档(NSCoding)
- SQlite3
- Core data

---



####应用沙盒 

每个应用都有自己的应用沙盒，文件夹

- 应用程序包
- Documents   运行时需要持久化的数据，iTunes会备份
- tmp   运行时的临时数据，使用完毕会删除
- Library/Caches  运行时需要持久化的数据
- Library/Preference  应用的所有偏好设置，会备份



```objective-c
// 获取沙盒主目录路径
NSString *homeDir = NSHomeDirectory();
// 获取Documents目录路径
NSString *docDir = [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) firstObject];
// 获取Library的目录路径
NSString *libDir = [NSSearchPathForDirectoriesInDomains(NSLibraryDirectory, NSUserDomainMask, YES) lastObject];
// 获取Caches目录路径
NSString *cachesDir = [NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES) firstObject];
// 获取tmp目录路径
NSString *tmpDir =  NSTemporaryDirectory();
```



---



####偏好设置（保存也是一个plist）

[NSUserDefaults standardUserDefaults]获取偏好设置对象

[defaults synchronize]调用立马写入文件