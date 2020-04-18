# 声明要求的cmake最低版本
cmake_minimum_required( VERSION 2.8 )


message(${CMAKE_CURRENT_LIST_DIR})

ADD_SUBDIRECTORY(${CMAKE_CURRENT_LIST_DIR}/accept_block)

ADD_SUBDIRECTORY(${CMAKE_CURRENT_LIST_DIR}/epoll_unblock)
ADD_SUBDIRECTORY(${CMAKE_CURRENT_LIST_DIR}/epoll_unblock_with_thundering_herd)