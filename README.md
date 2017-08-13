**Thread协议栈基础**

2015年7月

**修订记录**

| **调整** | **日期** | **注释** |
| :--- | :--- | :--- |
| 1.0 | 2014年11月29日 | 初始发行 |
| 2.0 | 2015年7月13日 | 公开发布 |

### 目录

[Introduction...................................................................................](#_bookmark0)

基本特性[...........................................................................................](#_bookmark1)

[IEEE 802.15.44...................................................................................................](#_bookmark2)

[无单点失效...................................................................................................](#_bookmark4)

[设备 Types5......................................................................................](#_bookmark5)

[边界路由....................................................................................................](#_bookmark6)

[Routers5...........................................................................................................](#_bookmark7)

[路由器资格终止 Devices5........................................................................................](#_bookmark8)

[困结束 devices6..................................................................................................](#_bookmark9)

[IP协议栈 Fundamentals6..................................................................](#_bookmark10)

[Addressing6.......................................................................................................](#_bookmark11)

[6LoWPAN7.........................................................................................................](#_bookmark12)

[ICMP7...............................................................................................................](#_bookmark14)

[UDP7................................................................................................................](#_bookmark15)

[网络 Topology8.................................................................................](#_bookmark16)

[网络地址和 Devices8.............................................................................................](#_bookmark17)

[网孔 Networks8..................................................................................................](#_bookmark19)

[路由和网络 Connectivity9...................................................................](#_bookmark20)

[MLE Messages9..................................................................................................](#_bookmark21)

[路由发现和 Repair10.............................................................................................](#_bookmark22)

[Routing14..........................................................................................................](#_bookmark28)

![](file:///C:\Users\jerry\AppData\Local\Temp\msohtmlclip1\01\clip_image002.gif)[重试和 Acknowledgements15.................................................................................](#_bookmark29)

[加入一个 螺纹Network15................................................................](#_bookmark30)

[Discovery15.......................................................................................................](#_bookmark31)

[Commissioning16................................................................................................](#_bookmark32)

[Attaching16........................................................................................................](#_bookmark33)

[MLE Messages17.................................................................................................](#_bookmark35)

[DHCPv618.........................................................................................................](#_bookmark36)

[Management18................................................................................](#_bookmark37)

[ICMP18.............................................................................................................](#_bookmark38)

[设备 Management18............................................................................................](#_bookmark39)

[一贯 Data19......................................................................................](#_bookmark40)

# 引言

## 基本特性

Thread协议栈是一个可靠，低成本，低功耗，无线D2D（设备到设备）的开放通信标准。它是为基于其中IP的联网期望和各种应用的层可以在栈上使用互联家庭应用而设计的。

这些都是Thread协议栈和网络的基本特点：

* 简单的网络安装，启动和运行：形成，连接和维护线程网络的简单协议，允许系统自行配置和他们发生解决路由问题。
* 安全性：设备不加入线程网络，除非授权，并且所有通信进行加密和安全。
* 小型和大型网络：家庭网络有所不同，从几个设备数百台设备的无缝通信。网络层的设计优化基于预期使用网络操作。
* 范围：与网状网络相结合的典型设备提供足够的范围，以覆盖一个普通家庭。扩频技术在物理层中使用，以提供良好的抗干扰性强。
* 无单一故障点：栈旨在提供安全可靠的操作，即使失败或单个设备的损失。
* 低功耗：主机设备通常可以用于在使用合适的工作周期AA型电池几年的运作。

[图1](#_bookmark3)示出了Thread协议栈的概述。

![](/assets/图1.Thread协议栈的概述.png)

**图1.Thread协议栈的概述**

## IEEE 802.15.4

该标准是基于IEEE 802.15.4[\[IEEE802154\]](https://standards.ieee.org/findstds/standard/802.15.4-2006.html)PHY（物理）和2.4GHz频带在250 kbps的操作的MAC（媒体访问控制）层。在IEEE 802.15.4-2006规格的版本用于Thread协议栈。

所述802.15.4 MAC层用于基本消息处理和拥塞控制。该MAC层包括CSMA（载波侦听多路访问）机制的设备以监听一个明确的信道，以及一个链路层处理的重试和相邻器件之间的可靠通信的消息的确认。MAC层加密和完整性保护，使用基于建立和软件栈的更高层配置的密钥的消息。网络层建立在这些潜在的机制来提供在网络中的可靠的终端对终端的通信。

## 无单一故障点

在由运行Thread协议栈设备的系统，所有这些设备的代表单个故障点。虽然有许多在执行特殊功能的系统中的设备，所述Thread协议栈的设计是这样的，它们可以在不影响被替换

线程网络内部正在进行的通信。例如，一个沉睡的孩子需要通信的家长所以这个家长代表失败的其通信的单点。然而，困设备能够而且将会如果其父是不可选择其他家长那么这个过渡应该不会对用户可见。

虽然该系统是专门为无单一故障点，在一定的拓扑结构会有不具有备份功能各个设备。例如，在与单个网关的系统中，如果网关断电，没有装置切换到替代网关。

路由器或边界路由器可以承担在Thread网络某些功能的一个领导者的角色。这位领导人需要使网络内的决定。例如，负责分配路由器地址，并允许新的路由器请求。领导者角色的当选，如果领导者出现故障，另一台路由器或边界路由器承担领导者的角色。正是这种自主操作，以确保有没有单故障点。

# 设备类型

## 边界路由器

边界路由器是一种特定类型的路由器从802.15.4网络上其它的物理层（例如，无线网络和以太网）相邻网络提供连接。边界路由器的802.15.4网络中的设备，包括关闭网络运营路由服务提供服务。有可能是在一个线程网络的一个或多个边界路由器。

## 路由器

路由器网络设备提供路由服务。路由器也试图加入网络的设备提供连接和安全服务。路由器不可睡觉。路由器可以降级它们的功能，成为芦苇（路由器资格的终端设备）。

## 路由器资格的终端设备

芦苇有可能成为路由器的能力，但由于网络的拓扑结构或条件下，这些设备不充当路由器。这些设备一般不将消息转发或在网络线程其他设备提供连接或安全服务。线程网络管理芦苇成为路由器如果有必要，而无需用户交互。

## 困终端设备

沉睡的终端设备是主机设备。他们只有通过沟通他们的母路由器，不能转发其他设备的消息。

# IP协议栈基础

## 解决

在指定的Thread协议栈支持IPv6寻址体系结构设备[\[RFC 4291\]](https://www.ietf.org/rfc/rfc4291)。设备配置1个或多个ULA（唯一本地地址）或GUA（全球单播地址）的地址。

启动网络的装置挑选一个/ 64前缀，然后在整个线程网络使用。前缀是局部分配的全球ID，常常被称为ULA前缀[\[RFC 4193\]](https://www.ietf.org/rfc/rfc4193)，并且可以被称为网格本地ULA前缀。线程网络还可具有每个可能或可能不会有那么可以用来产生额外的瓜斯前缀的一个或多个边界路由器。在Thread网络的设备使用其扩展MAC地址来导出其接口标识符作为在第6节中定义[\[RFC 4944\]](https://www.ietf.org/rfc/rfc4944)从这个配置与知名的本地前缀FE80 :: 0/64链路本地IPv6地址中的说明[\[RFC 4862\]](https://www.ietf.org/rfc/rfc4862)和[\[RFC 4944\]](https://www.ietf.org/rfc/rfc4944)。

该器件还支持相应的组播地址。这包括本地链路所有节点组播，链路本地所有路由器组播和领域，本地多播。

如在指定加入线程网络中的每个设备被分配一个16位地址短[\[IEEE802154\]](https://standards.ieee.org/findstds/standard/802.15.4-2006.html)。路由器，该地址被使用分配在与设置为0的低位比特的地址字段中的高比特，指示路由器地址。然后孩子们被分配使用他们的父母的高位，并为他们的地址相应的较低位的16位短地址。这使得线程网络的任何其他设备只需通过使用其地址字段的高位，以了解孩子的路由位置。

[图2](#_bookmark13) 说明螺纹短地址。

**图2.螺纹短地址**

## 6LoWPAN的

所有设备使用的6LoWPAN中定义 [\[RFC 4944\]](https://www.ietf.org/rfc/rfc4944) 和 [\[RFC 6282\]](https://www.ietf.org/rfc/rfc6282)。

报头压缩是线程网络内使用和设备传送消息压缩IPv6报头尽可能以最小化所发送的分组的大小。

如所讨论的网格报头被支承用于在网格内和用于链路层转发的消息的更有效的压缩[**路由和网络连接**](#_bookmark20)部分。mesh报头也允许端至端碎片的消息，而不是逐在指定跳碎片[\[RFC 4944\]](https://www.ietf.org/rfc/rfc4944)。Thread协议栈使用路由切换配置。

在指定的设备不​​支持邻居发现[\[RFC 6775\]](https://www.ietf.org/rfc/rfc6775)如DHCPv6用于地址分配给路由器。终端设备和芦苇由其母公司路由器分配的短地址。然后将该短地址被用于配置用于网络内的通信网的本地ULA。

在6LoWPAN的使用和配置的进一步详情载于白皮书“的6LoWPAN的线程使用”。线程规范的第3章详细介绍所使用的特定6LoWPAN的配置。

## ICMP

设备支持的ICMPv6（因特网控制消息协议版本6）协议[\[RFC 4443\]](https://www.ietf.org/rfc/rfc4443)及ICMPv6的错误消息，以及回波请求和Echo Reply消息。

## UDP

Thread协议栈支持UDP（用户数据报协议）中定义[\[RFC 768\]](https://www.ietf.org/rfc/rfc768)用于设备之间的消息传递。

# 网络拓扑

## 网络地址和设备

线程栈支持线程网络的所有路由器之间的全网连通。

实际的拓扑结构是基于路由器在网络线程的数量。如果只有一个路由器或边界路由器，则基本形成了星型拓扑结构有一个路由器。如果有一个以上的路由器然后自动形成一个网状拓扑。[图3](#_bookmark18)说明线程网络的基本拓扑结构和类型的设备。

![](file:///C:\Users\jerry\AppData\Local\Temp\msohtmlclip1\01\clip_image002.gif "Description: C:\work\Thread Group \(2015\)\\(2015\_T04\_002\) Thread Specification Writing\_2\white papers\figures\TSF\_Thread Basic Topology.png")![](/assets/基本主题的网络拓扑和设备.png)

**图3.基本主题的网络拓扑和设备**

## 网状网络

Mesh网络使允许无线电设备用于其它无线电将消息转发无线电系统更可靠。例如，如果一个节点不能直接将消息发送到另一个节点，网状网络通过一个或多个中间节点转发该消息。正如讨论[**路由和网络连接**](#_bookmark20)部，线程网络的性质是，所有路由器节点维护路由和连接彼此所以网格是不断保持和连接。通常存在的在Thread网络32个活性路由器的限制。然而，64个路由器地址被用来允许路由器地址的回收。在网状网络中，瞌睡终端设备或芦苇其他设备不路由。这些设备将消息发送到父是路由器。该母路由器处理其子设备的路由操作。

# 路由和网络连接

线程网络通常具有用于基于所述设备的路由表的消息的下一跳路由多达32个活性路由器。该设备的路由表被电池堆维护，以确保所有路由器都具有连接和高达最新路径在螺纹网络的任何其他路由器。的RIP（路由信息协议）算法（算法从

[\[RFC 1058\]](https://www.ietf.org/rfc/rfc1058)和[\[RFC 2080\]](https://www.ietf.org/rfc/rfc2080)但不是特定的消息格式）。所有路由器与其他路由器交换它们用MLE压缩格式路由到其他路由器在网络线程的成本（mesh链路建立）。

**注意：**从知识产权的角度看，螺纹网络支持路由器和主机。主机要么是困终端设备或簧片。

## MLE消息

MLE的消息（见[\[草案-凯尔-intarea目链路建立-06\]](https://datatracker.ietf.org/doc/draft-kelsey-intarea-mesh-link-establishment/)这是在第4章延长线，消息链路的建立，所述螺纹规格的）被用于建立和配置安全的无线链路，检测相邻设备，并保持在线程的网络设备之间的路由的成本。MLE消息使用单跳链路路由器之间的本地单播和多播传输。

MLE消息被用于识别，配置和固定联结到邻近设备作为拓扑和物理环境的变化。MLE还用于分发在跨越线程共享网络诸如信道和PAN（个人区域网）的ID的配置值。这些消息可以用简单的驱通过MPL（组播协议用于低功率有损网络）中指定的转发。（看到[\[草案-IETF-辊滴入MCAST-09\]](https://tools.ietf.org/html/draft-ietf-roll-trickle-mcast-09)了解更多信息。）

MLE消息也确保两个设备之间建立路由成本时，非对称链路的成本考虑。非对称链路成本是802.15.4网络中很常见。为了确保单向消息二是可靠的，考虑双向链路的成本是非常重要的。

## 路由发现和修复

在按需路由发现在低功耗802.15.4网络常用。然而，按需路由发现网络开销和带宽方面的成本由于路由发现请求充斥网络。

在一个线程网络，所有的路由器周期性地交换包含链路成本信息给所有的邻居路由器的单跳MLE通告报文和路径成本在Thread网络的其它路由器。通过这些周期性的，本地更新，所有的路由器都必须跟上时代的路径成本信息的任何其他路由器在网络线程，所以点播不需要路由发现。如果路由不再可用，路由器可以对到目的地的下一个最合适的路径选择。这种自愈路由机制允许路由器快速检测时，其他路由器都下车线程网络，并计算出最佳路径，以保持连接性的主题网络的所有其他设备。

在每个方向上的链路质量是基于从该邻近设备的传入消息的链路成本。这个呼入链路成本被映射到的链路质量从0到3的值0意味着未知成本。的链路成本是接收电平以上的接收消息RSSI（接收信号强度指示符）的测量。

[表格1](#_bookmark23)总结链路质量和链路成本。

**表1.链路质量和链路成本**

| **链路质量** | **链路成本** |
| :--- | :--- |
| 0 | 未知 |
| 1 | 6 |
| 2 | 2 |
| 3 | 1 |

[图4](#_bookmark24)说明线程网络上的各种链路成本的例子。

![](/assets/各种链路成本实例.png)

**图4的各种链路成本的实例线程网络上**

路径成本在Thread网络的任何其他节点则链路成本最小总和达到该节点。路由器监控这些成本，即使网络变化的无线链路质量或拓扑结构，并通过传播线程网络使用周期MLE通告消息新的成本。路由开销是基于两个设备之间的双向链路质量。

为了说明通过一个简化的例子，假设与在所有设备都在同一时间上电共享安全材料预委托网络。每个路由器将定期发送最初只与成本单跳邻居填充的广告。在内部，每个路由器将存储未在广告中发送的下一跳信息。

最初的几个广告，将有路径成本等于环节的成本，因为这是唯一已知的路由器是在说明近邻[图5](#_bookmark25)。

![](/assets/成型电后线程网络.png)

**图5.成型电后线程网络**

但随着路由器开始从他们的邻居包含成本是两个或更多的跳之外的其他路由器听到的广告，他们的桌子多跳路径成本填充，然后传播甚至更远的地方，直到最终出现在所有路由器之间的连接信息网络，如所示[图6](#_bookmark26)和[图7](#_bookmark27)。

![](/assets/主题网络形成：路由通告.png)

**图6.主题网络形成：路由通告**

![](/assets/主题网络形成：多跳.png)

**图7.主题网络形成：多跳**

当路由器从邻居接收到一个新的MLE的广告，无论是它已经用于该设备的邻居表项或一个加入。该MLE广告包含从邻居所以这是在路由器的邻居表更新传入的成本。该MLE

广告还包含其他路由器更新的路由信息​​，并且这些信息在设备中路由表的更新。

路由到子设备通过观察孩子的地址的高位来确定母路由器地址来实现。一旦设备知道母路由器，它拥有该设备的路径成本信息和下一跳路由信息。

活性路由器的数量被限制为可包含在单个802.15.4分组路由和成本信息的量。此限制是目前32个路由器但提供64活性的路由器地址，以允许老化出路由器地址。

## 路由

设备使用IP路由转发数据包。的装置的路由表被填充有网状本地地址ULA用于路由器和相应的下一跳的压缩形式。

距离矢量路由是用来获取路由路由器是线程网络上的地址。当线程网络上的路由，该16位地址的高6位定义了目的区路由器的路由器地址。如果目的地址的较低位为0，则该路由器是最终的目的地。否则，目标路由器负责把基于16位目标地址的低位的最终目的地。

为了路由超越线程网络，边界路由器通知特定的前缀（ES），它服务的领导者和该信息分布的MLE包内螺纹网络数据。线程网络数据包括：前缀的数据，这是前缀本身，6LoWPAN的情况下，边界路由器，并为前缀的DHCPv6服务器。如果设备配置使用前缀的IPv6地址，它使用SLAAC（无状态地址自动配置）或接触此相应的DHCP（动态主机配置协议）服务器。线程网络数据还包括路由服务器，这是默认的边界路由器的路由器地址的列表。

一个领导者指定的选择芦苇成为路由器或允许路由器恢复到芦苇做决定。该负责人还负责分配和管理路由器的地址。然而，包含在该路由负责人的所有信息出现在其他路由器，如果路由负责人不可达，另一台路由器自动当选，接任领导无需用户干预。

## 重试和确认

而UDP消息在Thread协议栈所使用的，可靠的消息传递仍是必需的。这是通过一系列轻巧的机制做如下：

·MAC级重试：每个设备从下一跳使用MAC确认和在MAC层，如果没有接收到MAC ACK消息将重试的消息。

·应用级重试：应用程序级可确定是否消息可靠性是关键参数，并且如果必要可以实现其自己的重试机制。

# 加入一个线程网络

![](file:///C:\Users\jerry\AppData\Local\Temp\msohtmlclip1\01\clip_image001.gif)

有一个连接装置必须经历才可以参加主题网络中的各个阶段：

* ·发现
* ·调试
* ·附上

所有加盟是用户发起的主题网络。一旦加入，将设备完全参与线程网络，可与内外线程网络与其他设备和服务的交换应用层信息。

**发现**

结合装置具有发现线程网络，并与调试路由器建立联系。接合装置扫描所有信道，发出各通道上的信标请求，并等待信标应答。信标包含包括网络的SSID（服务集标识符）和表示如果线程网是接受新成员的许可证接合信标有效载荷。一旦设备发现了主题网络，它使用MLE的信息来建立，通过它可以进行调试相邻路由器。

如果该设备已获得调试信息，因为它已经有足够的信息来直接连接到网络线程不需要发现。

**调试**

主题提供了两种调试方法：

* ·直接配置调试信息到使用了带外的方法的装置。调试信息允许加入设备尽快将其引入到网络连接到正确的线程网络。

* ·建立接合装置和智能电话，平板试运行的应用程序，或网络之间的调试会话。调试会话安全提供调试信息到连接设备，允许其在完成调试会话后连接到正确的线程网络。

**注意：**通过允许在信标有效载荷接合标志仅接合的典型802.15.4方法没有一个线程网络使用。这种方法是最常用的按钮式接合在没有用户界面或外的带外信道给设备。这种方法可能与在有多个网络可用，也形势设备转向问题可能有安全问题。

**附上**

与调试信息的结合装置，使具有父路由器接触，然后通过交换MLE链路配置消息附加到经由父路由器线程网络。设备连接到一个线程网作为任一终端设备或REED和分配由父路由器16位短地址使用中所示[图8](#_bookmark34)。

![](file:///C:\Users\jerry\AppData\Local\Temp\msohtmlclip1\01\clip_image010.gif "Description: C:\work\Thread Group \(2015\)\\(2015\_T04\_002\) Thread Specification Writing\_2\white papers\figures\TSF\_Attaching to a Network with Known Key.png")![](/assets/附加到线程网络与已知的钥匙.png)

**图8.附加到线程网络与已知的钥匙**

一旦里德连接，它可以紧接着将其分配由领导路由器地址可能发出一个地址请求成为一个路由器。

**MLE消息**

一旦设备连接到网络线程，有各种信息需要它来维持它在网络中的参与。MLE提供服务，整个邻居之间的网络交流环节的成本和安全框架柜台分发网络数据。

该MLE邮件分发或交换以下信息：

* ·相邻装置的16位短和64位EUI 64长地址
* ·设备能力信息包括：如果它是一个困端设备和所述困倦主机设备的睡眠周期
* ·邻居的链路成本（如路由器）
* ·设备之间的安全材料和帧计数器
* ·路由成本到所有其它路由器在网络线程
* ·更新网络数据，如在MAC中使用的信道，PAN ID和信标有效载荷参数

**注意：**MLE消息进行加密，除了发现在接合装置已经获得了所需的安全材料之前。

**DHCPv6报**

DHCPv6报[\[RFC 3315\]](https://www.ietf.org/rfc/rfc3315)是一个基于UDP的客户端 - 服务器协议来管理网络内的设备的配置。的DHCPv6使用UDP从DHCP服务器请求数据。

在边界路由器能DHCPv6服务用于配置：

* ·网络地址
* ·通过设备所需的多播地址
* ·主机服务

**管理**

**ICMP**

所有设备都支持的ICMPv6的错误消息，以及回波请求和Echo Reply消息。

**设备管理**

一个设备上的应用层可以访问一组设备管理和诊断信息，可以在本地使用或者收集并发送至其他管理装置。

从802.15.4 MAC层中使用由线程的信息包括：

* ·EUI 64个地址
* ·16位短地址
* ·能力信息
* ·PAN ID
* ·数据包发送和接收
* ·包掉在发送或接收
* ·安全性错误
* ·MAC重试次数

从网络层中使用由线程的信息包括：

* ·IPv6地址丢失
* ·邻居表
* ·子表
* ·路由表

**持久性数据**

在现场操作的设备可用于多种原因被意外地或故意复位。已重置设备，需要重新启动网络操作，无需用户干预。对于这个做需要一套信息被存储在非易失性存储器中。这包括：

·网络信息诸如PAN ID

·安全材料（每个键使用）

·从网络寻址信息以形成设备的IPv6地址

