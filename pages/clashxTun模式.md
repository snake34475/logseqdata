- ## 介绍
  
  	TUN/TAP是一种虚拟网络设备，通过此设备，程序可以方便得模拟网络行为，TUN模拟的是一个三层设备，通过它可以处理来自网络层得数据
  
  > 第一层为物理层，第二层是数据链路层，第三层是网络层，第四层是传输层
## 原理层
### 正常

![](https://cdn.jsdelivr.net/gh/snake34475/upload@main/img/202211081620847.webp)

	eth0是我们主机真是的网口（interface）与外部网络相连
​	收到的数据包会传递给内环网络协议栈（network stack）然后协议栈再对这些数据包进行进一步处理，确定数据为上层应用所需要，会通过socket api告知上层等待应用程序
### TUN工作模式

数据包处理过程

![1918847-85ea08bc89d9427e](https://cdn.jsdelivr.net/gh/snake34475/upload@main/img/202211081624198.webp)

完整部分

![1918847-92c47952b6f7fdd6](https://cdn.jsdelivr.net/gh/snake34475/upload@main/img/202211081626497.webp)

普通网卡是是通过网线来首发数据，TUN是通过文件来收发数据 /dev/tunX

tunX在这代表了一个网络接口通过软件模拟出来的
	网卡接口**tunx所代表的虚拟网卡通过文件/dev/tunX与我们得应用程序**相连，每次使用应用程序通过write写入，然后这些会以网络的方式通过虚拟网卡，同时也可以通过read方式调用读取

	也可以当做普通网卡使用，例如设定ip地址，路由，但是他不存在mac地址，因为只模拟到了网络层，在协议栈眼中，而tapX与网卡没有区别
### TAP

**TUN** 设备是一个三层设备，它只模拟到了 **IP** 层，即网络层 我们可以通过 **/dev/tunX** 文件收发 **IP** 层数据包，它无法与物理网卡做 **bridge**，但是可以通过三层交换（如 **ip_forward**）与物理网卡连通。可以使用`ifconfig`之类的命令给该设备设定 **IP** 地址。

**TAP** 设备是一个二层设备，它比 **TUN** 更加深入，通过 **/dev/tapX** 文件可以收发 **MAC** 层数据包，即数据链路层，拥有 **MAC** 层功能，可以与物理网卡做 **bridge**，支持 **MAC** 层广播。同样的，我们也可以通过`ifconfig`之类的命令给该设备设定 **IP** 地址，你如果愿意，我们可以给它设定 **MAC** 地址。
## clash的tun模式

其实tun和tap就是一个虚拟网卡，tap比tun模拟的更真实一点。
### 为什么用到tun模式

	因为有的软件翻墙也无法实现加速，所以需要让所有的流量走虚拟网卡，也就是全局翻墙模式，一般用于游戏中，目前tun和tap都可以实现

	浏览器之类的应用走的是系统代理，非系统代理应用可以通过设置被cfw接管。

TUN比TAP性能强一点（有待考证，如果是真的我认为是tun只模拟了网络层占用的较少）

优点
	- 提升clash处理UDP能力
	- 可以劫持任何三层流量，非常灵活实现dns劫持