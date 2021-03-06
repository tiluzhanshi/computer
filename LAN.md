### 局域网定义：
局域网LAN是将一个小较小地理范围内的各种计算机、通信设备等互相连接起来组成的一个计算机通信网络。一个局域网的跨度一般在方面几公理、几十公里以内，覆盖一栋办公楼、一个学校及至一个城市。

### 局域网发展历史：
20世纪70年代末，随着个人计算机硬件价格的急剧下降以及性能的不断提高，在企业和其他组织中，个人计算机得到了迅速发展。为了实现这些计算机彼此间的通信，并能共享这些个人计算机的各种软硬件及数据资源，局域网得到了广泛的应用，并发挥越来越重要的作用。




### 与广域网相比，局域网主要有以下特点
- 范围小。通常用于连接同一栋建筑物、同一个厂区、同一个城市的各种设备，一般覆盖距离小于25km。连接的主机数量也有限，不能太多（几百上千台主机就太多了）
- 速度快。局域网的组成及其所采用的技术决定了局域网和广域网相比有更快的传输速度，局域网的传输速率可以 达到100Mb/s、1000Mb/s、10Gb/s或者是更高。距离短传递的速率大。
- 低误码率。由于 局域网的地域范围有限、网络运行环境相对简单，有线局域网的误码率一般 为10的-8幂到10的-11幂
- 通常，局域网为一个单位所私有，仅为单位内部服务，并由单位独立建立和管理。这决定了局域在网络建立、网络安全、网络管理等方面与广域网有很大的区别

### 决定局域网性能差异的三个属性：
- 传输方式 
   - 在传输方式方面，局域网既可以使用基带传输（有线传输），也可以使用频带传输（无线传输）； 但从局域网的简单性以及性能等方面考虑，目前有线局域网大多采用基带传输方式。
   - 在信道连接方式方面，早期局域网大都采用广播方式传输，而目前越来越多的局域网采用点到点的方式进行传输。采用广播方式进行传输的局域网，需要解决的核心问题是介质访问控制方法，即解决共享信道的竞争问题，不同局域网的主要差异体现在采用了不同的介质访问控制方法。采用点到点方式进行传输的局域网，需要解决的核心总是是路由选择总是。


- 拓扑结构
   - 局域网典型的拓扑结构有：总线型、星形（最常用的拓扑结构）、环形（是IBM令牌环网，国内很少用，国外目前用的也少了）。这是局域网发展早期最常用的一种拓扑结构（第一代就是总线型以太网）。
   - 总线型：由于所有站点都连接在一条共享总线上，因此主要采用广播方式进行传输。
   - 星形：这种结构是局域网即可以使用共享的广播方式进行传输，又可以 使用交换的点以点方式进行传输，并且管理简单、组网灵活，因此是目前最常用的一种拓扑结构。
   - 环形：这种结构由于 对环路可靠性的依赖较大，主要在使用光纤作为传输介质的早期局域网中采用，例如：FDDI。
- 传输介质
   - 局域网常用 的传输介质有同轴电缆、双绞线、光纤以及无线介质。在局域网中传输介质的选择通常与拓扑结构以及传输方式的选择密切相关。例如：采用双绞线、基带同轴电缆、光纤的局域网一般采用基带传输； 而采用宽带同轴电缆、无线电波的网络一般采用频带（宽带）传输。 




### 网桥
工作在数据链路层的一种网络互连设备，这在互连的LAN之间实现帧的存储和转发。
根据MAC帧的目的地址对收到的帧进行转发。
网桥具有过滤的功能。当网桥收到一个帧时，并不是向所有的商品转发此帧，而是先检查此帧的目的MAC地址，然后再确定将该转发到哪一个接口。




### 网桥优点
- 过滤通信量
- 扩大了物理范围
- 提高了可靠性
- 可互连不同物理层、不同MAC子层和不同速率（如10M/s和100Mb/s以太网）的局域网


### 网桥缺点
- 存储转发增加了时延。
- 在MAC子层并没有流量控制功能（通过网桥连接的网段可能是异构的，所以他们传输速率不一致，发的慢收的快没有问题，当发的快收的慢就会有问题）。
- 具有不同MAC子层的网段桥接在一起时时延更大。
- 网桥只适合用户数据不太多（）和通信量不太大的局域网，否则有时还会因传播过多的广播信息而产生网络拥塞。这就是所谓的广播风暴。

### 网桥与集线器（物理层）区别：
- 集线器在转发帧时，不对传输媒体进行检测。
- 网桥在转发帧之前必须执行CSMA/CD算法
    - 若在发送过程出现碰撞，就必须停止发送和进行退避
    - 在这一点上网桥的接口很像一个网卡，但网桥却没有网卡
- 由于网桥没有网卡，因此网桥并不改变它转发的帧的源地址

### 透明网桥/生成树网桥
- 网桥工作在混杂方式；
- 网桥接收到一帧后，通过查询地址/端口对应表来确定是丢弃还是转发； 
- 网桥刚启动时，地址/端口对应表为空，采用洪泛方法转发帧；
- 在转发过程中采用逆向学习算法收集MAC地址。网桥通过分析的源MAC地址得到MAC地址与端口的对应关系，并写入地址/端口对应表。
- 网桥软件对地址/端口对应表进行不不断的更新，并定时检查，删除在一段时间内没有更新的地址/端口项。


### 透明网桥的帧转发帧的转发过程
- 目的LAN与源LAN相同，则丢弃帧； 
- 目的LAN与源LAN不同，则转发帧； 
- 目的LAN未知，则洪泛帧； 
- 均执行逆向学习（每接收一个数据帧都进行刷新）； 

### 全双工以太网
- 不再使用CSMA/CD
- 前提条件：  
    - 发送和接收信道必须使用分离的网络介质  
    - 任两个节点间须配备专门的链路  
    - 网卡和网桥交换机必须支持全双工方式
- 主要应用场合：   
   - 交换机到交换机的连接，它们之间通常有较远的距离   
   - 交换机到服务器的连接，以提高通往服务器的带宽   
   - 长距离节点间的连接


### 高速以太网
- 速率达到或超过100Mb/s的以太多称为高速以太网
- 在双绞线上传送100Mb/s基带信号的戥拓扑以太网，仍使用IEEE802.3的CSMA/CD协议，100BASE-T以太网又称为快速 以太网


### 100BASET特点
- MAC帧格式仍然是802.3标准规定的
- 保持最短帧长不变，但将一个网段的最大电缆长度减小到100m
- 帧间时间间隔从原来的9.6us改为现在的0.96us。
- 三种物理层类型   
   - 100BASE-TX   
   - 100BASE-FX   
   - 100BASE-T4



### 10吉比特以太网
- 与10Mb/s，100Mb/s和1Gb/s以太网的帧格式完全相同
- 不使用铜线而只使用光纤
- 只工作在全双工方式
- 物理层类型       
   - 局域网物理层：10.000Gb/s       
   - 可选广域网物理层：OC-192/STM-64              
      - 使10吉比特以太网的帧能够插入妻OC-192/STM-64帧的有效载载荷中，数据率为9.95328Gb/s。


### 虚拟局域网
- 虚拟局域网VLAN是由一些局域网网段构成的与物理位置无关的逻辑组。      
   - 这些网具有某些共同的需求      
   -  每一个VLAN的帧都有一个明确的标识符，指明发送这个帧的工作站是属于哪 一个VLAN
- 虚拟局域网其实只是局域网给用户提供的一种服务，而并不是一种新型局域网
- 虚拟局域网的优点 
   - 网络设备的移动，添加和个性的管理开销减少 
   - 可以控制广播风暴 
   - 可提高网络的安全性






### 局域网概述
- 局域网产生的原因      
   - 80年代，微型机发展迅速，彼此需要相互通信（近距离），共享资源；       
   - 功能分布：分布式计算，分布式数据库
- 局域网定义：是一种将小区 域内的各种通信设置互连在一起的通信网络（通信子网）



### 100BaseT和10BaseT比较
||10BASE-T|100BASE-TX|100BASE-FX|100BASE-T|
|--|--|--|--|--|
|编码方法|曼彻斯特 |4B/5B |4B/5B| 8B/6T|
|传输介质 |UTP3/4/5 |UTP5,STP1 |多模/单模光纤| UTP3/4/5|
|信号频率 |20MHz |125MHz |125MHz |25MHz|
|使用线对 |2对 |2对| 2对 |4对|
|发送线对 |1对 |1对| 1对| 3对|
|网段距离 |100m| 100m |150/412/2000m| 100m|
|全双工能力 |有 |有 |有 |无|


### IEEE802数据链路层划分子层的目的
- 将功能中与硬件相关的部分与硬件无关的部分分开，降低实现的复杂度。
- 局域网特点：共享信道（如总线）。需要解决介质访问控制（MAC）问题。子层划分可以使帧的传输独立于介质和MAC方法
    - LLC：与介质、拓扑无关
    - MAC：与介质、拓扑相关


### IEEE802网络体系各层功能
- 物理层功能 
   - 信号 的编码/译码
   - 前导码的生成/去除
   - 比特的发送/接收
- 数据链路层功能
   - MAC子层功能：成帧/拆帧，实现、维护MAC协议，位差错检测，寻址
   - LLC子层功能：向高层提供SAP，建立/释放逻辑连接，差错控制，帧序号处理，提供某些网络功能 。

### 逻辑链路控制子层LLC
- LLC帧格式（控制信息与HDLC大同小异）
- 服务访问点（SAP）
   - LLC SAP：向上层提供进程访问能力
   - MAC SAP：MAC地址（即：网卡地址）
- LLC提供的服务类型
  - LLC1  不确认无连接的服务
  - LLC2  面向连接的服务
  - LLC3  带确认无连接的服务
  - LLC4 高速传输服务（1991年专为城域网提出）




> LLC在今天的802.3中快没有了，被削弱了，LLC是屏蔽了MAC层的差异； 现在在市场上的网卡基本上都是以太网网卡，所以不需要使用LLC来屏蔽异构下面的MAC了

### 信道共享技术
- 计算机网络可以分成两类
   - 使用点到点连接的网络-----广域网
   - 使用广播信道（多路访问信道、随机访问信道）的网络-----局域网
- 解决信道急用的协议称为介质访问控制协议MAC（Medium Access Control）是数据链路层协议的一部分

### 信道的静态分配
- 信道多路复用FDM（波分利用WDM）
  - 原理：将频带平均分配给每个要参与通信的用户； 
  - 优点：适合于用户较少，数目基本固定，各用户的通信量都较大的情况； 
  - 缺点：无法灵活适应站点数及其通信量的变化。
- 时分多路复用TDM
   - 原理：每个用户拥有固定的信道传送时槽； 
   - 优点：适合于用户较少，数目基本固定，各用户的通信量都较大的情况； 
   - 缺点：无法灵活适应站点数及其通信量的弯。


### 信道的动态分配
- 动态分配定义：局域网都采用动态分配策略，即根据当前对信道请求的情况动态协调各用户对信道的使用权。
- 类型：冲突协议 和 无冲突协议

### ALOHA冲突协议
- 上世纪70年代，Norman Abramson设计了ALOHA协议
    - 目的：解决信道的动态分配，基本思想可用于任何无协调关系的用户争用单一共享信道使用权的系统； 
    - 分类：纯ALOHA	协议和时间片ALOHA协议
- 纯ALOHA协议
    - 基本思想：用户有数据要发送时，可以直接发至信道； 然后监听信道看是否产生冲突，若产生冲突，则等待一段随机的时间重发； 
- 时间片ALOHA协议
    - 基本思想：把信道时间分成离散的时间片，片长为一个帧所需的发送时间，每个站点只能在时间片开始时才允许发送。其他过程与纯ALOHA协议相同

![image.png](https://upload-images.jianshu.io/upload_images/5177180-10e84da89e5f96fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



### CSMA协议
- 载波监听多嘴访问协议
- 载波监听（Carrier Sense）
   - 站点在为发送帧而访问传输信道之前，首先监听信道有无载波，若有载波，说明已有用户在使用信道，则不发送帧以避免冲突。
- 多路访问（Multiple Access）
  - 多个用户共用一条信道
- 三个变种
   - 1-坚持型CSMA(1-persistent)
   - 非坚持型CSMA(nonpersistent)
   - p-坚持型CSMA（p-persistent）

### 1-坚持型CSMA
- 基本原理
   - 若站点有数据发慈禧太后，先监听信道
   - 若站点发现信道空闲，则发送
   - 若信道忙，则继续监听直至发现信道空闲，然后完成发送； 
   - 若产生冲突，等待一随机时间，然后重新开始发送过程。
- 协议特点
   - 优点：减少了信道空闲时间；
   - 缺点：增加了发生冲突的概率； 
   - 广播延迟对协议性能的影响：广播延迟越大，发生冲突的可能性越大，协议性能越关； 

### 非坚持型CSMA
- 基本原理
   - 若站点有数据发送，先监听信道； 
   - 若站点发现信道空闲，则发送；
   - 若信道忙，等待一随机时间，然后重新开始发送过程； 
   - 若产生冲突，等待一随机时间，然后重新开始发送过程； 
- 协议特点
    - 优点：减少了冲突的概率； 
    - 缺点：增加了信道空闲时间，数据改善延迟增大； 
    - 信道效率比1-坚持CSMA高，传输延迟比1-坚持CSMA大； 

### p-坚持型CSMA
- 适用于分槽信道
- 基本原理
   - 若站点有数据发送，先监听信道。
   - 若站点发现信道空闲，则以概率p发送数据，以概率q=1-p延迟到下一个时槽发送。若下一个时槽仍空闲，重复此过程，直至数据发出或时槽被其他站点所占用。
   - 若信道忙，则等待下一个时槽，重新开始发送；
   - 若产生冲突，等待一随机时间，然后重新开始改善。

### CSMA/CD
- 冲突
   - 当多个站同时在总线上发送数据时，总线上的信号电压摆动值将会增大（互相叠加）
   - 当一个站检测到的信号电压摆动值超过一定的门限值时，就认为总线上至少有两个站同时在发送数据，表明，产生了冲突。
- 冲突检测
   - 当两个帧发生冲突时，两个被损坏帧继续传送毫无意义，而且信道无法其他站点使用，对于有限的信道来讲，这是很大的浪费。
   - 如果站点边发送边监听，并在监听到冲突之后立即停止发送，可以提高信道的利用率，因此产生了CSMA/CD。

### CSMA/CD工作过程
- 站点使用CSMA协议进行数据发送； 
- 在发送期间如果检测到冲突，立即终止发送，并发出一个瞬间干扰信号，使所有的站点都知道发生了冲突； 
- 在发出干扰信号后，等待一段随机时间（称为退避），再重复上述过程； 


### 无冲突协议
- 基本位图协议（A Bit-Map Protocol）工作原理
   - 共享信道上有N个站，竞争周期分为N个时槽，如果一个站有帧发送，则在对应的时槽内发送比特1； 
   - N个时槽之后，每个站都知道哪个站要发送帧，这时按站序号发送。

### 令牌协议
- 网络中流转着一个被 称为“令牌Token”的帧，一个节点要发送数据必须首先截获令牌，由于网络中只有一个令牌，从而不会产生冲突。
![image.png](https://upload-images.jianshu.io/upload_images/5177180-d36c0ae7fef328e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 集线器示意图  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-ad876b288bfa1476.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 传统以太网
IEEE802.3和Ethernet
- 发展历史
  - ALOHA系统
  - ALOHA+载波监听
  - Xerox设计2.94Mbps的采用CSMA/CD协议的Ethernet
  - Xerox，DEC,Intel共同制定了10Mbps的CSMA/CD以太网标准
  - IEEE定义了采用1-坚持型CSMA/CD技术的802.3局域网标准，速率从1M到10Mbps，802.3标准与以太网协议略有差别。Ethernet和IEEE802.3的帧格式不同。

### 网卡
- 网络接口板又称为通信适配器（adapter）或网络接口卡NIC（Network  Interface Card）或网卡
- 网卡的重要功能 
   - 进行串行/并行转换
   - 对数据进行缓存
   - 在计算机的操作系统安装设备驱动程序
   - 实现以太网协议

### 网卡地址
- 在局域网中，硬件又称为物理地址 或MAC地址、网上地址。
- 802标准所说的“地址”严格地讲应当是每一个站的“名字”或标识符。
- 地址类型
   - 单播帧（一对一）
   - 广播帧（一对全体）
   - 多播帧（一对多）

![image.png](https://upload-images.jianshu.io/upload_images/5177180-b1bfca89659d03d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 网上连接  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-0e5e0d67c8f0cdcc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 网卡地址结构  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-9fbb42d2be24853b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 10BASE5连接示意  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-31c2f80c83059b0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 10BASE2连接示意  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-2ffe897a79af7e1e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 以太网最在作用距离   
![image.png](https://upload-images.jianshu.io/upload_images/5177180-7c62b8c283cd6604.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 以太网冲突示意过程  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-da57036168fdd55a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 急用期   
![image.png](https://upload-images.jianshu.io/upload_images/5177180-86d57bab25c92271.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 以太网急用期  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-ad0837f4e7c773bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 二进制指数后退算法
- 发生第一次冲突后，各个站点等待0或1个时槽再开始重传；
- 发生第二次冲突后，各个站点随机地选择等待0，1，2或3个时槽再开始等一会； 
- 第i次冲突后，再0至2<sup>i</sup>-1间随机地选择一个等待的时槽数，再开始等一会； 
- 10次冲突后，选择等待时的时槽数回写在0至2<sup>10</sup>-1之间； 
- 16次冲突后，发送失败，报告上层


### 最短帧长
- 如果发生冲突，就一定是在发送的前64字节之间； 
- 由于一检测到冲突就立即中止发送，这时已经发送出去的数据一定小于64字节； 
- 以太网规定了最短有效帧长为64字节，凡长度小于64字节的帧都是由于 冲突页异常中止的无效帧；

### 以太网V2的MAC帧格式  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-5eba27e1c96fccc8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/5177180-1efa5bc9be485a65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-fbd362880211bafe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### MAC帧格式示意  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-5b7f83a6a686178e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 帧间最小间隔  
![image.png](https://upload-images.jianshu.io/upload_images/5177180-1da7a9e3f58416c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### MAC帧格式
- 以太网MAC帧格式有两种标准
   - DIX Ethernet V2标准
   - IEEE 的802.3标准
- 最常用的MAC帧是以太网V2的格式

### 注意细节：
|注意细节|
|--|
|在80年代的用户数量少，所以才会使用网桥或中继器。|  
|网络规模比较大，用户数量比较，距离比较远就要用路由器进行组网  |
|网桥的接口不多，主要是用来连接网段。它是存储转发。  |
|以前的教材还是以以前的距离来划分局域网，对于现在来说并不准确了  |
|快速以太网是专用名词，特指百兆以太网； 千兆以太网是指高速以太网  |
|百兆以太网支持星型网络拓扑  |
|带宽为100Mb/s的以太网称为传统以太网，最早公布的传统以太网采用总线型拓扑。  
|早期的有显示器、键盘、通信机并不是一个计算机，仅仅是一个远端巨型机或大型上的一个附属终端，如果主机关机了，那么这些附属终端就没有任何作用了。  |
|广域网比局域网要发展的早，原因是和计算机的发展有关，先有设备的发展再有网络的技术。第一个公用分组交换网是X.25网，当时速率64K，ARPANET最初的连接美国的东西海岸线路。80年代的微型机发展迅速，共享资源是产生局域网重要因素。当时局域网之间基本上是相对独立的，孤立的。  |
|CSMA/CD冲突协议以及CSMA/CA冲突协议，这两种协议分别在CSMA的基础上增加了冲突检测和冲突避免机制，协议的具体实现将分别在以太网和无线网络中介绍  |
|以太网使用坚持式CSMA协议  |
|局域网最后一公里用的是双绞线|
|局域网有一个重要特征：共享信息（共享单一信道）|
|显示器、网卡、键盘、鼠标都需要驱动程序，现在一般都不需要手动安装。系统默认都安装了|



























