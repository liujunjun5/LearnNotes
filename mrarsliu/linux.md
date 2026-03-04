## 命令
1. 文件相关（mkdirs、mv、ls、rm）
2. 权限相关（chmod、groupadd）
3. 进程相关（ps、top）
4. 网络相关（telnet、ping、ip）

## ps
- pid
- ppid
- user
- time
- mem
- cpu

## top
1. 内存使用情况，空余、已使用情况 
2. 平均负荷
3. 交换空间使用情况
4. 进程列表（pid、ppid、内存、CPU占用情况）
5. 任务状态

## 如何删掉一个进程
1. ps找到pid  ps -ef | grep 进程名
2. kill pid

## 网络不连通用什么命令

## 如何知道有多少CPU

## 如何看端口被哪个线程占用

## 如何修改文件权限

## free和top的区别

## sed和awk的区别
sed 基础的文字替换、查找、删除  
awk sed的功能上添加条件循环

## 查找某一个字符的长度
grep | awk / wc

## 
sort -k3 -nr 日志文件 | head -n 10

## CPU 100% 如何处理
1. top查进程
2. ps查线程
3. jstack pid
4. 打印出的堆栈信息查看看原因

## 如何看系统负载
1. top
2. free


