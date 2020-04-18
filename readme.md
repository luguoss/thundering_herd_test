# 惊群效应测试
---
使用方式：
1. git clone 本工程
2. mkdir build && cd build
3. cmake .. && make -j 8
4. 启动一个模块的可执行文件 ./accept_block_wait_root_socket_listen_fd/accept_block
5. 测试连接： telnet 127.0.0.1 8888
---
## accept_block_wait_root_socket_listen_fd
此模块用于测试父进程开启socket进行监听，并fork若干子进程进行accpet阻塞等待 如果惊群效应存在， 则在连接后 服务端会打印n次收到信号 但仅一个fork进程accpet成功；
测试结果发现并不是这样，只有一个进行响应，而其他的三个进程并没有接收到请求， 这是因为linux 2.6内核已经解决了accept惊群的问题：
**大概的处理方式就是，当内核接收到一个客户连接后，只会唤醒等待队列上的第一个进程或线程。所以，如果服务器采用accept阻塞调用方式，在最新的Linux系统上，已经没有“惊群”的问题了。**