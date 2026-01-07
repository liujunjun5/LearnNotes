## 基本数据结构
map
1. Mutex
2. dirty
3. read
   1. amend
   2. readonly
      1. p（三种状态，nil，value，expunged）
4. missed

## 操作
### load
1. 读read
  1. 有——直接返回
  2. 没有&&amend==true——加锁访问dirty（双检状态）
     - 如果没返回nil
     - 有的返回value
     - missed+=1
2. missed >= len(dirty) 需要重建 

## 重建
 missed >= len(dirty) 需要重建 
 将dirty升级为read，dirty = nil

 如果发生store需要新增则重建dirty对nil，对value
## 特点
- 读多写少
- 空间换时间
- 高性能
## 简述
sync.Map 本质上是一个并发的map，map在并发读写场景下会直接报错，虽然可以直接使用Mutex锁方式简单粗暴的处理，但是性能差
这个背景下go1.9增加了sync.Map，将读写分离，用空间换时间的方式处理读写操作，read存储快照数据，让读写尽量无锁化。dirty存储全量数据，所有操作需要加锁。
