### 删除文件但是没释放

可能是进程还在写入而导致没释放，方法是不删除，直接清空这个文件`echo "" > a.log`，不仅可以马上释放，也可以保证继续写入。如果直接kill掉相关进程，可能会造成无法预估的问题

### 进程process和线程thread

一个cpu同时只能运行一个进程，一个进程可以包含多个线程

