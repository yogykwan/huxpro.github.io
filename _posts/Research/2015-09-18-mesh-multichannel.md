---
layout:     post
title:      "无线Mesh网络多信道技术"
subtitle:   ""
date:       2015-9-18
author:     "Jennica"
header-img: "img/post-bg-wifi.jpg"
catalog: true
tags:
    - 研究
    - 无线
---

#Optimal Multicast in Dense Multi-Channel Multi-Radio Wireless Networks
Rahul Urgaonkar, Prithwish Basu and Saikat Guha, Ananthram Swami

对稠密多信道多射频无线网络中的多播通信问题，Urgaonkar等人提出了两种基于分组思想的多项式时间复杂度的近似最优算法。他们首先利用特殊的网络拓扑推导出可能的最大吞吐量上届，然后利用修改TDMA帧时隙分配的算法传输多播。仿真表明，这两种算法都通过最大化每个多播组成员吞吐量的方式，达到了近似最优的效果。

#An adaptive load-aware routing algorithm for multi-interface wireless mesh networks
Zimian Hao • Yingxia Li

Zimian Hao等人提出了一种新的动态适应的信道度量值LAM（load-
aware metric），目的是解决由全网流量和内部流量互相干扰导致的链路负载不均衡的问题。并且，他们利用LAM扩展和改进AODV路由协议，设计了一种自适应的动态负载均衡按需路由算法LBRP（load balancing routing algorithm
）。LAM及LBRP可以根据网络拓扑和数据流改变而动态调整，避免节点瓶颈，选择最稳定和最低拥塞的链路去创建路由。以此，实现流量均衡，改善由拥塞和重传导致的高丢包率和高延迟问题。

#Improving Channel Assignment in Multi-radio Wireless Mesh Networks with Learning Automata
Mohammad Shojafar · Saeid Abolfazli · Habib Mostafaei · Mukesh Singhal

Mohammad Shojafar等人提出了一种基于链路层协议LLP和学习自动机的WMN信道分配算法LLLA（LLP and learning automata）。在LLLA信道分配算法中，LLP处于混杂模式，学习自动机为计算恰当的信道分配智能算法而服务。该智能算法的目的是找寻满足多种情境的最佳状态，根据网络需求、网络拓扑、应用动态自适应。媒介的初始状态由某数据集确定，然后依据从网络中收到的反馈改变状态。LLLA信道分配算法可以最小化全网干扰，从而提高网络容量。实验表明，在丢包、端到端延迟、特定应用的抖动、耗能等指标的对比下，LLLA比AODV协议更有效。

#Partially overlapped channel assignment for multi-channel multi-radio wireless mesh networks
Jihong Wang, Wenxiao Shi* , Keqiang Cui, Feng Jin and Yuxin Li

Jiong Wang等人基于部分重叠信道 POCs（partially overlapped channels），提出了一种与流量无关的信道分配算法POCA（partially overlapped channels assignment）。POCA算法由两步组成：邻居－接口绑定、接口－信道绑定。邻居－接口绑定：通过确定某个节点使用哪个接口与邻居交流，确定节点们之间的连接关系。接口－信道绑定：为使网络总的干扰最小化，确定一个确切的次序，并以此次序决定某个接口应该使用哪个信道。该算法可以为网络中所有链路分配信道，同时最小化网络干扰，从而提高网络容量。

#一种用于多信道无线Meh网络的信道分配方法
魏振春 吴亚伟 张本宏

魏振春针对动态信道分配策略平均吞吐率较低的不足，采用相对平衡理论，提出了一种基于可通邻居节点可用信道表的信道配方法ACLNN（ channel assignment method based on the available channel list of neighbour nodes）。节点在进行数据发送前，利用可通邻居节点的可用信道集合，建立可通邻居节点可用信道表和信道优先级队列，在此基础上，选取一个最优信道，用改进的RTS/CTS协议进行信道协商和数据收发控制 。该方法对于网络的平均吞吐率方面有所提高。

---

#A Multi-Objective Optimization Approach for Joint Channel Assignment and Multicast Routing in Multi-Radio Multi-Channel Wireless Mesh Networks
Elaheh Vaezpour · Mehdi Dehghan

 Elaheh Vaezpour等人将信道分配与多播结合，提出了一种基于多目标遗传算法NSGA-II的创新技术，建立一棵干扰最小的延迟制约最小花费多播树。该方法在花费、延迟和干扰方面在不同网络配置下都有较好的结果。

#An Efficient and Fair Strategy for Radio Resources Allocation in Multi-radio Wireless Mesh Networks
Lúcio Studer Ferreira · Luís M. Correia

Ferreira等人基于WMNs提出了一种分配策略LIRA（Load and Interference aware Resource Allocation strategy）。LIRA结合多种有效优化无线资源（速率、功率和信道），以保证每个聚合的Mesh接入点MAP的公平性。LIRA由速率适应和功率控制机制组成，对MWNs中的胖树流量特征非常敏感，在MAP网关处使用最高比特率，在分支使用满足容量需求的最低比特率。这可以有效的降低传输功率和干扰，有利于信道复用。LIRA还包含一个负载和干扰感知信道分配机制，使得所有链路同时运作而不出现干扰。当这个机制失效时，两个额外的机制，信道共享和无扰信道复用，可以通过降低特定MAP容量保证所有节点的公平性。LIRA的网关流量控制机制，保证了所有的MAP能够拥有分配的容量，以能够在最公平的状况下运行。通过仿真实验，LIRA策略被证明可以在网络成分混合的情况下，具有低低保率、低延迟和较高公平性的特点。

#MR-OLSR：多天线多信道无线Mesh网络中一种链路状态路由算法
张超钦 马江涛 胡光武

张超钦等人对Ad Hoc网络下的OSLR算法进行改进，提出多天线多信道无线网状网下一种优化的链路状态路由算法MR-OLSR，使得数据流可以在多路径上并行传输，实现拥塞避免和提高信道利用率的目的。利用改进的IWCETT测量尺度算法对多路径链路质量予以测量，同时根据路径质量提出的信道分配策略和多路径策略选择算法使得整体网络具有负载均衡的特性 。该算法在保持原算法鲁棒性和可扩展性的同时，进一步增强了单链路失效时的稳定性和可靠性, 提高了网络的吞吐率 。

 #Novel power-based routing metrics for multi-channel multi-interface wireless mesh networks
Marija Malnar • Natasa Neskovic • Aleksandar Neskovic

为解决室内环境下WMN中接收信号级别的大跨度问题，Marija Malnar等人改进了已有的路由度量值以及链路中的路径快速变换问题，将某个基于接收信号级别的参数分配给各个链路。将该参数与三种已知的度量值ETX（预计发送次数）、WCETX（加权累积ETT）和MIC（干扰和信道转换的度量）结合，提出了三种基于功率的新型路由度量值powerETX、powerWCETT和powerMIC。所有的度量值与多信道路由协议协同工作，并且在真是的室内环境中选取了恰当的聚合模型。通过新型度量值的使用，在不需要另外的硬件修改以及最小的软件修改的情况下，网络同样可以表现出更好的效果。

#Online Channel Assignment in Multi-Radio Wireless Mesh Networks Using Learning Automata
Ziaeddin Beheshtifard, Mohammad Reza Meybodi

Beheshtifard等人提出了一种基于学习自动机的新的信道分配方法，通过预期信道状态来适应性的提高网络总吞吐量。由于通过上行流量发包的能力可以作为给每个节点和接口分配信道的评估标准。使用一个链路容量函数来反映每个节点所选信道的干扰程度。根据系统的动态变化，该算法给无线接口分配信道，目标是最小化节点邻居间的干扰。在WMN中，配置了学习自动机的Mesh路由器，可以通过环境对于网络组件的上一次行为的反应，预测链路质量。这个发布特性使得在线信道分配，可以赋予网络最优的总吞吐量。实验表明，该算法可以大幅度提升网络效果并且很好的平衡网络连接和干扰。

#Interference Mitigation In Wireless Mesh Networks Through Radio Co-location Aware Conflict Graphs
Srikant Manas Kala, M Pavan Kumar Reddy, Ranadheer Musham, Bheemarjuna Reddy Tamma

由于冲突图是无线网络中不可或缺的演示和分析工具，Kala等人提出了一种与基础的冲突模型独立的冲突图MMCG（multi-radio multi-channel conflict graph
）的生成算法。同时他们提出了一个概念叫无线协同定位干扰RCI，表示多频射多信道WMN中由于空间协同定位导致的干扰。首先，他们证明了RCI对于WMN的表现具有负面影响。所以改进的MMCG模型有必要在传统MMCG模型的基础上加入消除RCI的方法。有效的信道分配策略可以通过扩充关于由RCI初始化的冲突链路的信息，有效缓解RCI的影响。结合4种信道分配策略的实验表明，MaIS-CA、CEN-CA改进效果比BFS-CA 和CLQ-CA更优。

#基于连接低干扰的无线Mesh网络信道分配算法研究
张伟昆, 黄炜, 张大伟

张伟昆等人针对无线Mesh网络的信道分配算法以连接低干扰信道分配算法（CLICA）为基础 ,以提高网络容量（吞吐量） 目为标提出了一种改进算法ECLICA （enhanced low interference channel assignment）。该算法根据 网络中各链路的干扰度来计算网络干扰度，通过减小网络的干扰度来提高网络吞吐量，以实现最小化网络干扰度的目标 。

---

#An Adaptive Channel Scheduling Design for Multi-Hop Handoff Delay Reduction in Internet-Based Wireless Mesh Networks
Haopeng Li, Student Member, IEEE, and Jiang Xie, Senior Member, IEEE

Haopeng Li等人从一个全新的角度看待无缝切换，提出了一种基于有向天线的分层WMN信道分配算法HiCA（hierarchical channel assignment）。通过将分层网络结构中的组件组成一个个团，减小竞争区域，使得每个团内的信道可以被复用。在HiCA中，切换信号包和数据包的保留或传输被协调至不同的时间段，所以信道之间的竞争被消除了。而信道资源的使用由团中的领导节点控制，这样就解决了多信道中的隐藏终端和信道选择问题。同时，HiCA中引入了一个适应性的信道保留机制，以解决之前多信道MAC协议中存在的控制信道瓶颈问题。由于适应性的加入，控制信道的信道保留时间可以被降低，以此提高信道利用率。该算法减小多跳无线链路中切换信号排队延迟和媒介介入延迟，同时提高了信道的平均利用率。

#A novel measurement-based approach for modeling and computing interference factors for wireless channels
Alper Rifat Ulucinar, Ibrahim Korpeoglu1 and Ezhan Karasan2

对于相邻信道互相干扰的问题（如多信道无线Mesh网络的信道分配），Ulucinar等人以理论和实验的的方式提出了一种模型用于定量计算重叠，即两个无线信道间的干扰。文中提出基于物理层的测量、技术独立和普遍性方式，来确定不同无线技术间的干扰因子，如IEEE 802.11和IEEE 802.15.4。通过展示802.11b DSSS信道、802.15.4信道和802.11b信道间的干扰因子的测量结果，可以知道该方法是可以实施的、准确的而且具有足够的一般性，可以计算不同无线通信技术的无线信号的干扰因子。

#Asymptotic Throughput Capacity Analysis of Multi-Channel, Multi-Interface Wireless Mesh Networks
Mohammad Mansoori · Mehdi Mahdavi

Mohammad Mansoori等人基于多信道基建WMN中每个节点的接口数少于信道数的场景下，提出了一种新的非线性吞吐量研究方式。分析表明，吞吐量的结果依赖于接口数和信道数。为了获得高吞吐量，多信道多接口基建WMN需要部署恰当数量的无线Mesh路由器和网关，而在路由器和网关之上有需要配置恰当数量的接口。

#An Efficient Interference Aware Partially Overlapping Channel Assignment and Routing in Wireless Mesh Networks
Sarasvathi V, N.Ch.S.N. Iyengar, Snehanshu Saha

由于基于部分重叠信道POC的信道分配算法赋予了无线频谱共享更多的灵活性，Sarasvathi V等人首先结合POC将信道分配问题描述为一个图边界的染色问题。当一个信道被分配给某个链路时，测量信噪比以避免邻居传输的干扰。他们随即提出了一种新的路由度量值叫做SINR（signal-to-noise plus interference ratio），用于评测每个链路的干扰，并提出了一种基于干扰信息的干扰感知路由算法。该算法在改善网络性能和增加网络吞吐量方面都有较好的表现。

#LAMR: learning automata based multicast routing protocol for multi-channel multi-radio wireless mesh networks
Mohsen Jahanshahi · Mehdi Dehghan · Mohammad Reza Meybodi

Mohsen Jahanshahi将多播问题与信道分配问题结合考虑，提出了一种基于学习自动机的多播路由协议LAMR（Learning Automata based Multicast Routing protocol）。在分发操作中，每个节点接口处的学习自动机决定该接口所使用和邻居通信的信道及频射。首先，从多播源到每个多播接收者的最小延迟路径被预处理计算得到，以此相比之前的算法能更节约时间。然后，学习自动机以最小冲突为目的来初始化多播树。同时，LAMR还可以解决终端隐藏的问题。实验表明，在获得的吞吐量、端到端延迟、平率发包率和多播树总花费等方面，该算法比之LCA和MCM都有更好的表现。

#Links organization for channel assignment in multi-radio wireless mesh networks
Hongju Cheng & Naixue Xiong & Laurence T. Yang & Guolong Chen & Xiaofang Zhuang & Changhoon Lee

为使得WMN中能给实时多媒体应用最好的支持，Hongju Cheng等人提出了一种基于PSO（Particle Swarm Optimization）的信道分配算法DPSO。网络中的链路可以被组织，并且最小化同信道干扰的方式分配非正交信道。同时，他们提出了两种启发式信道分配算法：CHA（Centralized Heuristic Algorithm）和DHA（Distributed Heuristic Algorithm），分别基于中心控制和分布式。与基于紧急搜索算法的信道分配算法相比，在小型网络的场景下，他们所提出的这几种信道分配算法都可以得到更好的近似最优解。

#Load-balanced Multicast Tree Routing in Multi Channel Multi Radio Wireless Mesh Networks Using a New Cost Function
Avid Avokh · Ghasem Mirjalily

为解决多频射多信道的无线Mesh网络（MRMC-WMN）的多播负载均衡问题，Avid Avokh等人首先引入了一种新型的负载感知动态花费函数去评价网络的链路。该函数在考虑无线广播优点的同时，也会考虑到负载均衡的问题。接着，他们提出了一种平衡多播树路由算法LMTR（Load-balanced Multicast Tree Routing），并使用到了上述定义的花费函数。该算法不仅最小化了传输数量，而且可以在节点间公平的分散流量以减小网络中的冲突，同时权衡负载与延迟的关系。LMTR算法大幅度的避免了网络中瓶颈的产生，并且减小了Mesh路由器中流量负载的标准差。

#Network coding for multiple unicast sessions in multi-channel/interface wireless networks
Alireza Shafieinejad • Faramarz Hendessi • Faramarz Fekri

无线网络的吞吐量限制可以使用两种解决方案，一是使用正交多信道，二是使用网络编码NC。由于已有的启发式理论工作都只关注了传统的传输／IP／MAC结构中的信道分配设计问题，而NC在无线多跳网络中可以提高单播的吞吐量，Shafieinejad等人提出了一种多信道多接口无线网络中融合NC、路由和信道分配问题的解决方案。首先，他们将单播模式下的NC扩展为包含COPE-type模式的NV，并命名为Star-NC。然后，他们提出了一种分析架构可以同时优化路由、信道分配和网络编码问题。基于线性规划LP的理论公式为寻找源到目的路由以及使用最恰当的NC策略去最大化总吞吐量提供了方法。基于这个LP，他们提出了一种新的信道分配算法，可以同时兼顾编码机会和共信道干扰。仿真表明，NC可以提高多信道网络的容量。

#On the number of channels required for interference-free wireless mesh networks
Aizaz U Chaudhry, John W Chinneck and Roshdy HM Hafez

为解决WMN中最小无覆盖频率信道的问题，Chaudhry等人基于已有的拓扑控制算法TCA建立联通图CG。该算法可以通过控制Mesh节点的邻居大搞控制网络连接的效果，以此实现最小的传输总功率和最大的信道复用，并达到通过提高信道的空间复用来减小所需信道的数量的目的。而在最大功率下，基于TCA的联通图方式比传统建立CG的方法要求的信道数更少。使用多路径路由实现网络的最大吞吐量，结果比传统的基于功率的最短路算法在吞吐量方面有所提升。同时，他们提出了有效的启发式方法来确定无干扰信道分配中所需的最小信道数量，在NCR和LCR方面基于MaIS的启发式信道分配算法要优于基于MIS的启发式信道分配算法。

#On the Relationship Between Transmission Rate and Network Capacity in Multi-Radio Multi-Channel Wireless Mesh Networks
Ji-Hoon Yun

Yun在论文中基于混合整数线性规划，定量考察了多频射多信道无线Mesh网络中物理层传输速率和网络容量的关系，并兼顾了信道分配及路由问题。数值结果表明，比最高可达到速率低的传输速率可以提高网络的吞吐率，因为它增加了网络的连通性。而且，低速率由于在信道分配方面具有更高的自由度，因此可以更有效的利用足够多的信道。综合考虑速率、信道分配和路由问题可以有效提升网络效果。

#多信道IEEE802.11无线Mesh网络中路由度量算法研究
何萍实 ,徐子平 , 杨峡

针对两种典型的路由度量算法RTT（round trip time）和EXT（expected transmission count），何萍实等人对他们进行了分析，比较了其在选路上的优缺点 , 并据此提出一种可以全面综合反映路由带宽和时延的新的路由度量算法WERTR（weighted expected residual transmission rate）。该算法使用瓶颈链路的期望剩余传输率决定一条路由的优劣，而其对瓶颈链路的定于为期望剩余传输率最小的链路，而不考虑链路使用的哪个信道。通过实例比较了WERTR和RTT、EXT的性能，验证了其有效性。

---

#An energy efficient channel assignment and routing algorithm for multi-radio wireless mesh networks
S. Avallone

针对WMN中鲜有提及的功耗这个NP难问题，S. Avallone观察到监听一个帧的耗能几乎与接收一个帧持平，所以他提出了一种启发式算法找寻最优的可行解路由给出的流量命令并通过信道分配打开无线信号。在不损害网络容量的前提下，通过最打的关闭状态无线信号数量以节约能耗。同时，他提出了两种能够最优解决上述问题的混合整数线性规划方法。

#A new channel, power and rate assignment algorithm for multi-radio wireless mesh networks
Stefano Avallone · Francesco Paolo D’Elia · Giorgio Ventre

由于之前针对信道分配和路由的无线启发式算法的做法与有线无异，并未充分考虑无线网络的特性，Avallone等人提出了一种信道、功率和速率分配的启发式算法FCPRA（Flow-based Channel, Power and Rate Assignment）。该算法充分考虑在无线链路调节传输功率和速率的影响，目的是提高信道分配的效率。在该算法中，提高传输功率会导致新链路的链接，而新的链路必须分配新的速率，这对流量传输速率的计算依赖非常大，现有的计算方式并不能满足目的，所以他们还需要一种更有效的速率算法。但即便如此，在现有的模型下，该启发式算法FCPRA比之前的算法LACA（Load-Aware Channel Assignment）和BSCA（Balanced Static Channel Assignment）据有更好的效果。

#A taxonomy of cross layer routing metrics for wireless mesh networks
Md Asri Bin Ngadi , Saqib Ali , Abdul Hanan Abdullah and Rashid Hafeez Khokhar

由于现有的WMN路由和路由度量协议是基于移动Ad Hoc网络，而WMN具有很多不同的特性和限制，所以WMN中QoS和吞吐量的提升可以通过跨层路由方法。Md Asri Bin Ngadi等人在路由参数、传输速率、流内干扰、流间干扰、拥塞和信道分化方面，针对不同的路由度量协议进行分类和比较。这些协议包括ETX、mETX、ENT、ETT、IETT、MD、WCETT、MIC、Airtime Cost、LAWARE、INX、LAETT、WCETT-LB、RARE、CATT、ILA、CWB、MIND、C2WB。该文章，为进一步研究多频射多信道无线Mesh网络中高吞吐量IP的连接跨层路由度量协议开辟了道路。

#Cooperative Multi-Channel Access for 802.11 Mesh Networks
Shashi Raj Singh and Mehul Motani

由于之前多信道接入技术集中在路由层和MAC层，并且主要是通过分析和仿真来研究，Shashi Raj Singh等人提出了一种解决802.11Mesh网络多信道介入问题的算法DISH（distributed information sharing）。他们将DISH融入IEEE 802.11 DCF的设计扩展了802.11 MAC协议，并使用802.11硬件设备和开源的Linux驱动实现了该扩展协议。该论文综合讨论了协议设计需要注意的事项、实现的挑战性和Mesh真实测试平台下得到的实验结果，证明了高强度流量情况下该技术的优越性，以及多信道接入是提高802.11 Mesh网络表现的有效技术。


#Optimization model for handoff-aware channel assignment problem for multi-radio wireless mesh networks
Jihene Rezgui, Abdelhakim Hafid, Racha Ben Ali, Michel Gendreau

为保证最大吞吐量的同时，综合考虑其他影响移动的无线网络连接的因素，如公平性和切换，Rezgui等人提出了一种多目标优化模型。首先，使用Jain论文中的索引列表最大化用户间公平性，同样的高负荷的切换时允许分配相同的信道，这样就降低了切换导致的高延迟的重新路由引发的效率低的问题。接着，他们提出了一种集中式的不同邻居搜索和禁忌搜索启发式算法（MHALB+/MTABU+），将提出的模型转化为了离线信道分配过程。进一步，为了适应由于用户切换导致的网络动态变化，基于不断最小化重新路由延迟的想法，他们提出了一种在线的信道分配方式将信道重新分配给每个接口。并且，利用负载平衡优化了该该在线信道分配方式。该模型在延迟、丢包率、总吞吐量和公平性方面都具有较好的表现。 

#Using Orthogonal Channels for Supporting Multicast Service in Multi-channel Wireless Mesh Networks
Abbas Nargesi and Mehdi Ghasemi

与有线网络不同，无线网络的容量严重受限于由无线媒介的广播特性导致的网络干扰，为充分利用WMN的容量和多播问题，Nargesi等人提出了一种分布式建立多播树的算法EWM（Efficient Wireless Multicast）。该算法使用分布的方式选取中继节点，并将正交无线信道分配给它们。为了进一步降低增加树枝的带来的干扰，从广播源节点出发具有最小端到端延迟的路由会被优选，所以该算法适合于多媒体应用。同时，为减小中继节点的数量，论文仔细研究了无线媒介的广播特性并将其加以改进利用。

---

#信道分配

##单接口多接口
###单接口
###多接口
####静态
####动态
####混合
####干扰感知
####速率

##静态动态混合
####静态
####动态
####混合

##集中分布
###集中
###分布

##正交重叠
###重叠

##单播多播
###单播
###多播

##其他分类
###忙音
###规定信道分配
###博弈
###整数线性规划
