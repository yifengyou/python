# yield

## 作用

* 把函数包装为generator。然后可以对该generator进行迭代: ```for x in fun(param)```
* 可以把yield的功效理解为暂停和播放;在一个函数中，程序执行到yield语句的时候，程序暂停，返回yield后面表达式的值，在下一次调用的时候，从yield语句暂停的地方继续执行，如此循环，直到函数执行完
* 生成器是迭代器，这种迭代器只能迭代一次。生成器不会将所有值都存储在内存中，它们会动态生成这些值
* yield是一个与return类似的关键字，只是函数将返回一个生成器。


```
>>> def createGenerator():
...    mylist = range(3)
...    for i in mylist:
...        yield i*i
...
>>> mygenerator = createGenerator() # 创建一个生成器
>>> print(mygenerator) # 生成器是一个对象
 <generator object createGenerator at 0xb7555c34>
>>> for i in mygenerator:
...     print(i)
0
1
4
```


## 区别生成器、迭代器


* 所有你可以用"for... in ...."的类型都是迭代器



## 生成器实现多任务



##









---
