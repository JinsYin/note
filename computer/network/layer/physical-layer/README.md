# 物理层（Physical Layer）

物理层确保原始数据可在各种物理媒介上传输。

## 功能

1. 为数据端设备提供传送数据通路
2. 传输数据

## 电脑连电脑

两台电脑相连可以构成一个最小的局域网（**LAN**）。

流程：

1. 网线一头插在 PC1 的网卡上，另一头插在 PC2 的网卡上
2. 网线的水晶头要做交叉线（1-3、2-6 交叉接法）
   2.1 水晶头的 `1、2` 脚 和 `3、6` 脚，分别起到收、发信号的作用
   2.2 将一端的 1 号线和 3 号线、2 号线和 6 号线互换位置
3. 两台电脑都需要配置 `IP 地址`、`子网掩码`、`默认网关`，且必须配置成同一个网络（如：192.168.0.2/24 和 192.168.0.3/24）

## 集线器（Hub）

* 与交换机不同，集线器没有大脑，完全工作在物理层
* 集线器收到的每一个字节都会广播到其他端口上去
