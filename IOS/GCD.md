### GCD

纯C语言，自动管理线程的生命周期

参考链接：[GCD参考](https://juejin.im/post/5a90de68f265da4e9b592b40#heading-22)



####任务和队列

dispath_sync()  只能在当前线程中执行任务，没有开线程能力，同步函数，只有把队列中的任务完成

dispath_async()  可以在新线程中执行任务



并发队列，多个任务同时执行（自动开启多个线程），只有在dispath_async中有效

串行队列



#### 创建队列

1. 手动创建队列

   DISPATCH_QUEUE_CONCURRENT 并发队列

   DISPATCH_QUEUE_SERIAL或NULL 串行队列

   ``dispatch_queue_t queue=dispatch_queue_create("队列名称", 队列类型);``

2. 获取全局并发队列

   ``dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT(优先级), 0);``

3. 获取主队列

   ``dispatch_get_main_queue();``

   主队列是GCD自带的特殊串行队列，任务都会放在主线程中执行

   在主线程中使用同步函数和主队列会死锁，因为主队列发现主线程有任务在执行，会暂停调度，导致死循环



***

#### GCD其他方法

1. **GCD 栅栏方法：dispatch_barrier_async**

   ***栅栏函数不能使用并发队列***

   我们有时需要异步执行两组操作，而且第一组操作执行完之后，才能开始执行第二组操作。这样我们就需要一个相当于 **栅栏** 一样的一个方法将两组异步执行的操作组给分割起来，当然这里的操作组里可以包含一个或多个任务。这就需要用到`dispatch_barrier_async`方法在两个操作组间形成栅栏。 `dispatch_barrier_async`函数会等待前边追加到并发队列中的任务全部执行完毕之后，再将指定的任务追加到该异步队列中。然后在`dispatch_barrier_async`函数追加的任务执行完毕之后，异步队列才恢复为一般动作，接着追加任务到该异步队列并开始执行。具体如下图所示：

   ![image-20190118165109584](/Users/efun/Documents/Notes/IOS/assets/image-20190118165109584.png)

   

2. **GCD 延时执行方法：dispatch_after**

   需要注意的是：`dispatch_after`函数并不是在指定时间之后才开始执行处理，而是在指定时间之后将任务追加到队列中。严格来说，这个时间并不是绝对准确的，但想要大致延迟执行任务，`dispatch_after`函数是很有效的。

   

3. **GCD 一次性代码（只执行一次）：dispatch_once**

   我们在创建单例、或者有整个程序运行过程中只执行一次的代码时，我们就用到了 GCD 的 `dispatch_once` 函数。使用 `dispatch_once` 函数能保证某段代码在程序运行过程中只被执行1次，并且即使在多线程的环境下，`dispatch_once`也可以保证线程安全。

   

4. **GCD 快速迭代方法：dispatch_apply**

   通常我们会用 for 循环遍历，但是 GCD 给我们提供了快速迭代的函数`dispatch_apply`。`dispatch_apply`按照指定的次数将指定的任务追加到指定的队列中，并**等待全部队列执行结束**。

   

5. **GCD 的队列组：dispatch_group**

   - 调用队列组的 `dispatch_group_async` 先把任务放到队列中，然后将队列放入队列组中。或者使用队列组的 `dispatch_group_enter、dispatch_group_leave` 组合 来实现 `dispatch_group_async`。

   - 调用队列组的 `dispatch_group_notify` 回到指定线程执行任务。或者使用 `dispatch_group_wait` 回到当前线程继续向下执行（会阻塞当前线程）。

   - **dispatch_group_notify** : 当所有任务都执行完成之后，才执行`dispatch_group_notify` block 中的任务。

   - **dispatch_group_wait** : 暂停当前线程（阻塞当前线程），等待指定的 group 中的任务执行完成后，才会往下继续执行。

   - **dispatch_group_enter、dispatch_group_leave** : 

     - `dispatch_group_enter` 标志着一个任务追加到 group，执行一次，相当于 group 中未执行完毕任务数+1

     - `dispatch_group_leave` 标志着一个任务离开了 group，执行一次，相当于 group 中未执行完毕任务数-1。
     - 当 group 中未执行完毕任务数为0的时候，才会使`dispatch_group_wait`解除阻塞，以及执行追加到`dispatch_group_notify`中的任务。





