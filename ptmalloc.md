小块内存从堆上分配，大块内存使用mmap动态分配。

每个arena从一个或多个堆上获取可分配的内存。main arena使用进程空间初始的堆，其它的arena调用mmap分配堆内存。

堆中的chunk要么被分配给了应用，要么是空闲待分配。待分配的chunk按照大小和最近使用存放在各种有序链表中，便于在需要分配时快速找到合适的chunk，这些存放chunk的链表称为bin。

>内存延迟分配，用户态程序使用malloc分配内存时，是分的虚拟内存，只有真正访问内存时，才建立虚拟内存到物理内存的映射。
>求证一下这一点

##### 参考链接
1. [The GNU Allocator](https://www.gnu.org/software/libc/manual/html_node/The-GNU-Allocator.html)
2. [malloc实现原理](https://sourceware.org/glibc/wiki/MallocInternals)
3. [Glibc内存管理--ptmalloc2源代码分析](https://blog.csdn.net/iteye_7858/article/details/82045969)