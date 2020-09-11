小块内存从堆上分配，大块内存使用mmap动态分配。

每个arena从一个或多个堆上获取可分配的内存。main arena使用进程空间初始的堆，其它的arena调用mmap分配堆内存。

##### 参考链接
1. [The GNU Allocator](https://www.gnu.org/software/libc/manual/html_node/The-GNU-Allocator.html)
2. [malloc实现原理](https://sourceware.org/glibc/wiki/MallocInternals)