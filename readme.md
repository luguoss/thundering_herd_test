# 惊群效应测试
使用方式：
1. git clone 本工程
2. mkdir build && cd build
3. cmake .. && make -j 8
4. 启动一个模块的可执行文件 ./accept_block_wait_root_socket_listen_fd/accept_block
5. 测试连接： telnet 127.0.0.1 8888
## accept_block_wait_root_socket_listen_fd
此模块用于测试父进程开启socket进行监听，并fork若干子进程进行accpet阻塞等待 如果惊群效应存在， 则在