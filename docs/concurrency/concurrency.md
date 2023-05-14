```
System.out.println("hello");
```



核心问题
+ 分工  
  如何高效的拆解任务并分配给线程  
+ 同步  
  线程间如何协作
+ 互斥  
  如何保证同一时刻只允许一个线程访问共享资源  
JAVA SDK 包含处理这三个核心问题，并发容器和原子类

## 分工
### JAVA SDK并发包 
+ Executor  
+ Fork/Join  
+ Future
这些同时也可以解决线程协作即**同步**问题
### 并发设计模式
+ 生产者 - 消费者  模式  
  优点：  
  1. 生产者一个一个地生产数据，而消费者可以批处理，提高了性能
+ Thread-Per-Message  模式
+ Worker Thread 模式

## 同步
JAVA并发解决协作(**同步**)的核心：**管程**; 是一种解决并发问题的通用模型, 可以解决线程**协作**和**互斥**问题。
### JAVA SDK并发包
+ CountDownLatch  
+ CyclicBarrier  
+ Phaser  
+ Exchanger
+ Executor 分工+同步
+ Fork/Join 分工+同步  
+ Future 分工+同步

## 互斥
线程安全: 内存模型和互斥

### 内存模型
解决以下问题
+ 可见性问题  
+ 有序性问题  
+ 原子性问题

### 互斥
核心: 锁(Lock)  
+ synchronized  
+ ...

引入锁保证了安全性问题，但降低了性能。同时保证安全和性能，分场景优化:  
#### 性能问题: 
+ 优化读多写少场景锁的性能  
  ReadWriteLock ，StampedLock
+ 无锁数据结构：原子类
+ 不共享变量或者变量只允许读
  + Thread Local
  + final
  + Copy-on-write 模式
#### 死锁问题:
+ ...

可见性: 了解一些CPU和缓存知识  
原子性: 了解一些操作系统知识  
无锁算法: 理解CPU缓存

![并发编程全景图-思维导图](./_media/java/并发编程全景图-思维导图.png)