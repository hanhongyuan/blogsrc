---
title: ceph中monitor数量
date: 2019-02-14 12:12:28
tags:
- ceph
---

# monitor作用

ceph中mon作用主要是保存ceph集群中的各种图，ceph客户端和集群交互的第一步是先和mon交互。因此mon就很重要。ceph原生支持mon高可用，通过使用Paxos算法来进行主备切换。

<!--more-->

# monitor数量讨论

mon数量推荐为奇数，而且增加也是两个一组进行增加。当mon的数量不够法定的数量时，ceph命令就会卡住。

| mon数量 | 允许down的最多个数 | down多少个异常 |
|--|--| -- |
| 10 | 4 | 5 |
| 9 | 4 | 5 |
| 8 | 3 | 4 |
| 7 | 3 | 4 |
| 6 | 2 | 3 |
| 5 | 2 | 3 |
| 4 | 1 | 2 |
| 3 | 1 | 2 |
| 2 | 0 | 0 |
| 1 | 0 | 0 |


# ceph-ansible操作

经测试经过下面流程可以进行建立集群

第一台mon->第二台mon->第一台mgr->第一台osd

当然上面可以一次执行完全装完。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI5ODYzMjIxOSwxNjc5NjYyNjYwXX0=
-->