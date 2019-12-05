刚装好，没有连接控制器的OVS是这样的：

```shell
[root@power28 ovs]# ovs-ofctl -OOpenFlow13 --no-names --sort dump-flows "$@" ovsbr
 cookie=0x0, duration=13930.318s, table=0, n_packets=1484, n_bytes=246728, priority=0 actions=NORMAL
```

NORMAL的意思应该就是交给传统交换机的处理流程去处理。在VM里Ping一下，n_packets数量就会增加。此时使用GRE隧道可以让不同主机的两台VM进行通信。？？？？

一旦连上控制器，就会下发许多流表项下来。