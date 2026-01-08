## defer 是什么
defer func()
作为函数的关键字，延迟函数的执行，一般用于收尾垃圾清理。
后进先出的顺序
## defer的作用
资源回收，锁释放
## defer的结构
- 延迟的函数
- 标志位
  - 内嵌
  - 堆上
  - 栈中
- _defer链表

## defer的执行过程 and recover
### return
赋值return，defer，返回return
### panic
panic 中断函数
是否有defer
是否recover
## 三种实现
堆上：维护链表，堆上分配，性能差

栈中：维护链表，函数生命周期

内嵌：开启编译优化，defer<=8,defer加返回语句乘积小于18，不在循环中
