### NSOperation

配合使用**NSOperation(操作)**和**NSOperationQueue(队列)**

创建操作--->创建队列--->添加操作到队列



**NSOperation子类**

- NSInvocationOperation

  单独使用毫无作用

- NSBlockOperation   

  可追加任务

- 继承NSOperation自定义子类实现相应方法  

  重写main方法，有利于代码复用





**NSOperationQueue**

**主队列**	[NSOperationQueue mainQueue] 和GCD的主队列一样

**非主队列**    [[NSOperationQueue alloc]init]   同时具备并发和串行的功能，默认情况下非主队列是并发队列，可以设置最大并发数，最大并发数为1是串行队列。



[queue addOperationWithBlock:] 简便方法：内部创建操作，并把操作加入队列

串行队列可暂停、取消

暂停只能当当前任务执行完才会暂停队列，不会中断当前正在执行的任务，可继续执行

取消不可恢复，内部调用所有操作的cancel方法



**操作依赖**

[*op1* addDependency: *op2* ]   任务1会等待任务2执行完才执行，还可以跨队列依赖



**操作监听**

op1.completionBlock = ^{}  监听操作完成 



线程间通信  



