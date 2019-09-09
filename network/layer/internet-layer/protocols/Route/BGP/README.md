# BGP 协议

**BGP**（英文：Border Gateway Protocol，边界网关协议）

BGP 构建在 EGP 的经验之上。

## 自治系统

在网络世界中，这一个个国家成为自制系统 **AS**（Autonomous System），自治系统分几种类型：

| 类别          | 描述                                                    | 适用范围         |
| ------------- | ------------------------------------------------------- | ---------------- |
| Stub AS       | 对外只有一个连接，不会传输其他 AS 的包                  | 个人或小公司网络 |
| Multihomed AS | 可能有多个连接连到其他 AS，但大多拒绝帮其他的 AS 传输包 | 大公司网络       |
| Transit AS    | 有多个连接连到其他 AS，并且可以帮助其他的 AS 传输包     | 主干网           |

每个自治系统都有边界路由器，通过它可以和外面的世界建立联系。

## 分类

BGP 分为两类：**eBGP** 和 **iBGP**。

![eBGP & iBGP](../../.images/eBGP&iBGP.png)

自治系统间，边界路由器之间使用 `eBGP` 广播路由。
自治系统内，通过运行 `iBGP`，可以使边界路由器从 BGP 学到的路遥导入到内部网络，从而使得内部路由器能够找到到达外网目的地的最好边界路由器。