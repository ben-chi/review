* 用户线程VS内核线程：用户线程创建销毁消耗少，不需要走内核（用户态和内核态的切换），不消耗内核线程资源（内核能创建的内核线程有限），但是内核不感知用户线程，一个用户线程的阻塞会导致整个进程的阻塞（一人有难，全家牵连），而且分到的时间片也会被分给所有的用户线程（多人只分到一块蛋糕）执行时间短

* gmp：https://go.cyub.vip/gmp/gmp-model.html

* dont repeat yourself

* User --> user cache --> page cache --> disk :一般的缓冲，非直接IO

* 直接IO：User --> user cache -->  disk  (不走内核缓冲page cache，直接调设备驱动)

  * https://cloud.tencent.com/developer/news/406991

* 阻塞 I/O：等待「内核数据准备好」和「数据从内核态拷⻉到⽤户态」这两个过程

* 文件系统：http://c.biancheng.net/view/3066.html

* innodb使用b+ tree，不使用跳表原因：https://juejin.cn/post/7106131535857713160

* DMA（Direct Memory Access） 功能，它可以使得设备在 CPU 不参与的情况下，能够⾃⾏完成把设备 I/O 数据放⼊到内存. Cpu-->DMA-->device<-->memory

* 键盘键入字符的发生事情：键盘设备缓存字符，向cpu发起**硬件中断**，cpu响应中断，(DMA?)从键盘设备读取字符至内存，进入中断处理函数：**放到「读缓冲区队列」**，显示设备的驱动程序会定时从「读缓冲区队列」读取数据放到「写缓冲区队列」（如果有写文件操作，大概也是去读「读缓冲区队列」？），最后把「写缓冲 区队列」的数据⼀个⼀个写⼊到显示设备的控制器的寄存器中的数据缓冲区，最后将这些数据显示在屏幕 ⾥。

* linux发送网络包过程：application --> socket发送缓冲区 --> 网络协议栈 -->网卡 ----------> 网卡 --> 网络协议栈 --> socket接收缓冲区 -->application

* 零拷贝：https://zhuanlan.zhihu.com/p/83398714

  * 在⾼并发的场景下，针对⼤⽂件的传输的⽅式，应该使⽤「异步 I/O + 直接 I/O」来替代零拷⻉技 术
  * 传输⽂件的时候，我们要根据⽂件的⼤⼩来使⽤不同的⽅式： 传输⼤⽂件的时候，使⽤「异步 I/O + 直接 I/O」； 传输⼩⽂件的时候，则使⽤「零拷⻉技术」

* 一致性hash：https://segmentfault.com/a/1190000021199728

* I/O 多路复⽤：

  * select

    * **最大限制：**单个进程能够监视的文件描述符的数量存在最大限制
    * **时间复杂度：** 对socket进行扫描时是线性扫描，即采用轮询的方法，效率较低，时间复杂度O(n)
    * **内存拷贝：**需要维护一个用来存放大量fd的数据结构，这样会使得用户空间和内核空间在传递该结构时复制开销大
    * 阻塞式调用

  * poll

    * **没有最大连接数的限制**。（基于链表来存储的）
    * 其余同select

  * epoll

    * **没有最大连接数的限制**
    * **时间复杂度低：** 边缘触发和事件驱动，监听回调，时间复杂度O(1)。
    * **内存拷贝：**利用mmap()文件映射内存加速与内核空间的消息传递，减少拷贝开销。
    * **边缘触发：**只有**新数据**到来才触发
    * **⽔平触发：**只要有数据就触发
    * ET模式在很大程度上减少了epoll事件被重复触发的次数，因此效率要比LT模式高

  * 多路复⽤ API 返回的事件并不⼀定可读写的，如果使⽤阻塞 I/O， 那么在调⽤ read/write 时则会发⽣程序阻塞，因此最好搭配**⾮阻塞 I/O**，以便应对极少数的特殊情况。

    > Under Linux, select() may report a socket file descriptor as "ready for reading", while nevertheless a subsequent read blocks. This could for example happen when data has arrived but upon examination has wrong checksum and is discarded. There may be other circumstances in which a file descriptor is spuriously reported as ready. Thus it may be safer to use O_NONBLOCK on sockets that should not block.


* Reactor模型
  * Reactor 负责监听和分发事件，事件类型包含连接事件、读写事件；
  * 处理资源池负责处理事件，如 read -> 业务逻辑 -> send；
  * 单 Reactor 单进程 / 线程：**Redis**：EventLoop
    * 不适⽤计算机密集型的场景，只适⽤于业务处理⾮常快速的场景
    * 无锁

### Mysql

* 组提交机制
  * 秒杀中减轻mysql压力
  * mysql中redo log和binlog写盘时降低磁盘压力
* crash safe
  * 依赖于redo log + binlog，利用两阶段提交确保一致性
* redo log作用
  * crash safe
  * 写数据库的时候，不用每次都刷盘，可以安心放在内存中（还是crash safe
* binlog格式：row（用的多，另外可以用于快速恢复）、statement
* mysql集群架构：一主一备多从
* 从库的并行复制
  * 经典策略：同库、同表、同行的放在一个worker中执行
  * MariaDB 的并行复制策略：能够在同一组里提交的事务，一定不会修改同一行；主库上可以并行执行的事务，备库上也一定是可以并行执行的。
* 主从延时导致的不一致
  * 强制走主库（取巧
  * sleep一段时间（取巧
  * GTID保证一致性
* 临时表
  * 一个临时表只能被创建它的 session 访问，对其他线程不可见，在 session 结束的时候，会自动删除



### Go

* Type、Value和Kind
