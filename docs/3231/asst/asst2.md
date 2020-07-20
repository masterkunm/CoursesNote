* VFS open成功以后我们会得到一个vnode struct, 同一个文件返回用一个vnode struct, 注意打开文件以后的偏移量，fork()后两个进程同时访问，fp.referenceCount + 1(open file table). ofptr要放在进程的struct中。

* 下面这个宏分别调用vnode_check, 和后面vn结构中的函数，#sym换成对应字符串，##sym连接前面。

![img](../../../img/Screen%20Shot%202020-07-10%20at%2010.14.16%20pm.png)

