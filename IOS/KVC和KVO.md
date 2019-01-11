### KVC和KVO

####key value coding(KVC)

1.赋值

- 赋值 setValue: forKey:  和setValue: forKeyPath:

  KeyPath可以内部点语法

- 可以修改类的私有成员变量
- setValuesForKeysWithDictionary 字典转模型，根据字典的key赋值对象的属性，字典转模型(但不建议使用，字典的key值和对象属性必须一样 )

2.取值

valueForKey: 和 valueForKeyPath:

3.模型转字典

dictionaryWithValuesForKeys:模型属性数组 

4.取出数组中所有模型的某个属性值

arr valueForKeyPath:key



####Key Value Observing(KVO)

监听对象属性值

addObserver:观察者(给谁观察) forKeyPath:属性 options:选项 context:上下文

去除监听

removeObserver:观察者 forKeyPath:属性



被监听的属性改变，观察者会调用方法

-(**void**)observeValueForKeyPath:(NSString *)keyPath ofObject:(**id**)object change:(NSDictionary<NSKeyValueChangeKey,id> *)change context:(**void** *)context

keyPath 被监听属性

object 被监听的对象

change 改变的信息

context 上下文