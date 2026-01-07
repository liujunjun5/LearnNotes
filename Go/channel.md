## channel是什么
channel管道，用于GO中的数据传递，区别于Java的共享内存读写，GO使用GSP模型，用管道管理多个grountine的数据传递
分为缓冲管道（初始化看有没有带指针类型）和无缓冲管道（初始化本身结构内存）
## channel数据结构
本质上是一个环形数组
* qcount
* size
* recvq/sendq
* sendp
* recvp

* sudog封装等待的模型
  * g
  * nxt
  * pre
 
## channel操作原理
### 读取
1. 是否为nil
2. 获取锁
3. 是否有sendq
4. 是否缓冲数据
5. 释放锁
### 写入
1. 是否nill
2. 获取锁
3. 是否有recvq
4. 是否缓冲数据
5. 释放锁
### 删除
1. 判断是否已经为nil panic
2. 获取锁
3. closed == 1 释放锁 panic
4. 对于接收队列 返回零值，优雅的让其继续运行
5. 对于发送队列，明确表示panic
