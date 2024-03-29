---
title: Reputation-Based Sharding Consensus Model in Information-Centric Networking
abbrlink: 46627
date: 2022-04-12 16:56:02
categories:
tags:
description:
top:
---

<p align="right">副标题</p> 

## 摘要



## 

## 关键词

区块链； 信息中心网络；分片；声誉；共识；



<!-- more -->

## 研究问题

### 研究背景(简要介绍)

​	介绍区块链技术和信息中心网络的集成，讲述区块链存在的交易效率的问题和现有的解决方法，其中重点介绍了几种分片机制和现有分片机制的问题，

### 研究问题或解决技术问题描述（需定位和描述清晰）

​	这篇文章结合SEANet网络可以提供的优势特征如节点之间存在信息交互的特性、网内AE模块的计算能力以及确定性时延解析服务（可以提供分布式、现场的、服务时延保障的ID-NA解析服务）进行建模仿真，基于网内节点对网络贡献度指标（如转发次数、丢包率、命中次数）等角度提取声誉信息，提出了一种多维声誉模型来提高区块链节点的可信度。

​	信誉值由信任参数计算，包括服务质量（QoS）、安全质量（QoSec）、评估信誉、过去信誉和推荐信誉。多维度的声誉值利用客观信任、主观信任和历史信任的角度衡量声誉价值，保证了高声誉价值不能通过欺骗获得，任何新节点都无法通过在短时间内表现良好而显著提高声誉价值。

​	避免了现有声誉评价中由于只考虑区块交易中的行为、对社区的贡献、评论维度的主观评价而带来的合谋或垄断等安全风险。此外，还提出了一种基于网络拓扑的分片划分方案来优化分片组的共识传输过程，以减少共识验证时延。该分片方案通过信誉值和网络距离计算出的总相似度参数，可以实现分片之间的信誉和网络距离的均匀分布。同时，我们也引入名称解析系统为分片的注册和查询提供优势，帮助快速有效地分发交易等事务。













## 研究现状

### 围绕研究问题，进行相关研究成果列举（注明参考文献）

​	对于目前区块链中六种最著名和最典型的分片机制，即Monoxide[101], Elastico[93], OmniLedger[94], Rapidchain[95], Chainspace[102], 和Ethereum 2.0[103]，分片方案大都是基于随机性的，即定期重新洗牌一致共识节点，随机分组以确保系统的安全性。

​	随机方案要满足良好的随机性，即需要满足几个重要的属性，不偏置性、不可预测性和公共可验证性。目前提出的抗偏差的分布随机性方案主要有以下几种：（1）基于PoW的随机方案。在弹性节点中，每个节点在PoW哈希中竞争以获得其身份，然后所有节点被随机分配到不同的碎片[104] (2) RandHound和RandHerd[105]。通过在(t，n)阈值安全模型中提供抗偏差的公共随机性，该模型已经在阈值密码学[106]、[107]和拜占庭共识协议[108]中广泛使用。（3）Algorand [109]。提出了一种基于委员会的共识协议，该协议使用可验证的随机函数(VRF)[110]，以委员会成员的账户余额（即股份），以私人和非互动的方式进行加权。然而，这些都不容易实现。产生公众的随机性是困难的，因为积极的对手可能会不诚实地使公众的随机选择偏向他们的优势。



​	研究者们开始引入了基于信任的分片分配算法，以便根据节点的信任分数在分片之间分配节点。在分片和领导人选举过程中使用的信任分数可以将恶意攻击的对手影响降至最低。[113] 提出了一个信任模型，该模型通过统计共识过程中每个节点同行评审的汇总结果来评估信誉。[114] 介绍了一种新的信誉方案，利用了一个分层的链结构来分别记录交易和声誉。通过一个单独的声誉链更新每个节点的声誉。声誉方案是基于每个节点对共识过程所作贡献中的有效工作。为了确保分片子链的安全，[115,116]增加了声誉评估维度，该维度基于对等方客户的可信度，即与同一分片中的对等方关联的客户，而不仅仅是对共识过程的评估。同时，新的分片聚类方法也受到了研究人员的关注。[117]使用自适应对冲算法[100]进行分片组选择。它是一种决策论在线学习方法，根据最佳策略最小化共识节点的累积损失。[99]基于遗传算法（GA）设计了基于信任的分片分布（TBSD）模型，为分片分布的优化问题提供了足够好的解决方案。基于改进的遗传算法计算最优分片分布，通过探索各种解空间快速找到近似解。[98]提出了一种基于K-Means算法的地理邻近感知聚类（GPSC）方法，以降低构建整个网络拓扑的复杂性，该方法基于著名的K-Means算法将一致性节点分为多个分片簇。这些分片分配方案在一定程度上优化了简单随机分配方法的安全性和效率，但仍然忽略了节点间的异构性。在不考虑节点间服务质量的情况下，对节点的评价信誉进行聚合。这些能力较差的共识节点可能会成为瓶颈，阻碍系统吞吐量。



### 研究现状总结，及现有研究仍然存在不足或问题

现有的解决方案不能使区块链像所需要的那样扩展到数百或成千上万的参与者[111]。如果没有良好的随机性，区块链系统的安全性就会被破坏。即使有良好的随机性，区块链系统也可能很容易受到破坏。例如，通过一个复杂的攻击，如贿赂攻击[112]，对手可能有能力控制整体计算能力的临时多数（例如，超过50%），这反过来可能会破坏整个系统。

## 思路特色

### 与现有研究（技术手段）不同之处

​	基于上述调查结果，我们提出本文基于声誉的分片共识模型，并利用亲和传播（AP）算法将共识节点聚集到分片中。考虑到最小的犯错动机和对验证安全性的可量化信心，客户可以在保证安全性的情况下实现实时处理速度的需求。在下一小节我们将对我们的具体方案进行详细描述。

## 关键问题/技术点

### 围绕研究题目，提炼出需要解决的几个关键问题点/技术点

本研究点的主要贡献如下：

（1） 我们提出了一种新的多因素信任模型用于一致性共识中的共识参与节点的信誉评估。这些评估参数将从客观信任、主观信任和历史信任的角度衡量声誉价值，从而将恶意节点通过合谋和欺骗改善声誉的概率降至最低。

（2） 分片分配方案通过亲和传播算法（Affinity Propagation，AP）进行优化。设计新的余弦相似度输入的计算方法。聚类结果很好地考虑了分片内网络距离的减小。所有分片集群在网络中均匀分布，而不是聚集在一个域中。同时，我们的模型还最小化了恶意节点在分片之间的分布，以提高基于分片的区块链的安全性。

（3） 用OMNET++进行了实验分析。仿真结果表明，我们的声誉方案的估计声誉值与真实声誉值之间的归一化均方误差（NMSE）小于0.02，这证明了我们的声誉评估机制的可靠性。同时，在1000个节点的大型联盟区块链网络的情况下，TPS性能可以达到经典分片OmniLedger方案的1.4倍。

## 解决方案

### 总体解决方案（最好能画一个总体方案图、或有一段描述清楚总体思路）

我们给出了基于声誉的分片模型的架构设计，对关键组件的实现方法进行了定义，并详细描述了模型的安全性和合理性。系统模型如图3.2所示。关键组件包括三个部分：声誉统计、导出和分发分片节点的分组结果、查找用于并行处理事务的可用分片。

![image-20220424165757562](https://gitee.com/josephucas/pcc-beed/raw/master/img/image-20220424165757562.png)





### 每个问题点/技术点分别的解决方案或模型设计

#### 声誉机制

​	声誉统计：声誉数据可以通过网络边缘计算进行收集、处理和验证，由网内的分布式算力提供一个分布式的信任管理系统支持，该系统监控共识节点的行为，以管理和计算声誉值。边缘数据的聚合可以通过SDN技术来实现，为分片的计算提供有效参数。

​	分片机制增加了区块链网络的可扩展性，但也增加了恶意攻击的影响。为了解决这个问题，研究人员引入了共识节点的信任模型来提高分片和选举过程的安全性。然而，现有研究中的信任模型多基于节点在区块交易中的行为、对社区的贡献、评论等来计算声誉价值。这些维度基于区块链中其他节点的主观评价，而没有考虑网络层共识节点的网络特征。合谋攻击或垄断攻击等安全风险的存在使得这些方案无法提供足够的信任。

​	因此，我们设计了声誉评分的多因素信任模型，该模型将信任参数扩展到服务质量（QoS）、安全质量（QoSec）、评估信誉、过去信誉和推荐信誉。这些评估因素将从客观信任、主观信任和历史信任的角度衡量声誉价值，如图3.3所示。我们的模型保证了两个重要问题，即声誉价值的积累需要一定的时间，而高声誉值不能通过欺骗获得。任何新节点都无法通过在短时间内表现良好而显著提高声誉值。同时，如果可信共识验证节点被检测为行为不端，它将失去系统中的所有声誉积累值，其身份将被列入黑名单。所有其之前验证的交易都将被重新检查，恶意行为的成本非常昂贵，因此保证可信验证节点在任何情况下都没有不当行为的动机。

![image-20220424170924047](https://gitee.com/josephucas/pcc-beed/raw/master/img/image-20220424170924047.png)





导出和分发分片节点的分组结果：通过SDN技术获取分片计算的声誉参数和网络距离参数，进行聚类参数和聚类算法的计算，从而得到维持公平分片分布的最优分片聚类集并完成结果的分发





查找用于并行处理事务的可用分片：分片注册、解析和交易承诺如图3.2的步骤1-3所示。共识阶段中的每个分片的消息广播主节点在本地SNR中使用其ID-NA注册。当事务验证请求提交给客户端节点时，它们从SNR请求最近分片的主节点的网络NA地址，以找到最近的可用分片集。





## 实验设计&结果分析

### 场景选择、实验设计、指标选取

​	数据安全：考虑到数据传输和存储的安全性，使用加密技术（如RSA、ECC）对重要信息和消息进行加密和签名。本文不讨论安全方案数据。默认情况下，数据的传输和存储不能被篡改。

​	共识协议：在每个分片内部使用的共识协议是PBFT（实用拜占庭容错）。同时，我们参考了文献[76]中提出的可信性证明（Proof-of-Believability，PoB）的方法。该协议将每个分片内部中的所有共识验证节点分为两组，即可信共识组和普通共识组。可信验证组在第一阶段快速处理事务。之后，普通验证组在第二阶段对交易进行采样和验证，以更高的安全性。节点被选入可信共识组的概率由可信度分数决定，在我们模型中的可信度分数即是声誉分数值。

​	跨分片交易：如上所述，我们在本研究点中不关注跨分片交易。文献[118-122]中提出的跨分片交易方案可与本方案进行结合



### 实验结果分析



## 论文结论

### 得出文章结论

一般般吧，优点是在icn网络中有了声誉机制

缺点是



1. 没有介绍这种声誉机制中的声誉值是怎么计算的，只是用了别人已有的声誉值
2. 这里面介绍的ap分片算法的计算复杂度过高，在工业实践方面根本就没有可行性
3. 这里面的声誉机制的互通本来就有一个bug那就是存在一个独立的声誉评测机构



