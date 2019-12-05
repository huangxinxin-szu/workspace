[TOC]

## 使用GRE隧道技术连接两台虚拟机

power27  10.222.111.11 ovs-tap0 5900

power28  10.222.111.12 ovs-tap0 5902

在host1上执行：

```sh
ovs-vsctl add-br br0

virsh define ovs-tap0.xml
virsh start ovs-tap0

virsh define ovs-tap1.xml
virsh start ovs-tap1

ovs-vsctl add-port br0 gre0 \  # 建立JRE通道
    -- set interface gre0 type=gre options:remote_ip=<IP of eth0 on host2>
```

