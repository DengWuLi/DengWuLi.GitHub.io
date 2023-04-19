---
title: 'Computer Networks Part Answers 3 - 2'
index_img: /img/ComputerNetworksCover.jpg
banner_img: /img/ComputerNetworksCover.jpg
date: 2023-04-19
tags:
  - ComputerNetworks
category:
  - AnswersShare
---
# Computer Networks Part Answers 3 - 2

<font face = "Times New Roman" size = 4>
<b>11.</b> A channel has a bit rate of 4 kbps and a propagation delay of 20 msec. 
For what range of frame sizes does stop-and-wait give an efficiency of at least $ 50 \% $?
</font>
由停等协议效率公式: $$ \eta = \frac{I}{ I + 2bR }$$
其中 $ I $ 是帧长, $ b = 4kbps, R = 20ms  \eta = 50 \% \Longrightarrow I \geq 160bits $

<br>

<font face = "Times New Roman" size = 4>
<b>12.</b> A 3000-km-long T1 trunk is used to transmit 64-byte frames using protocol 5. 
If the propagation speed is 6 μsec/km, how many bits should the sequence numbers be?
</font>

假定序号为 $ n $位, GobackN 协议的最大发送窗口 $ W = 2^n - 1 $
其信道利用率公式为: 
$$ \eta = \frac{W}{1 + 2a} \quad a = \frac{传播时延}{发送时延} \quad \eta = 100 \\% $$
$ 传播时延 = 3000 \times 6 = 18 ms, \\; 发送时延 = 64 \times 8 \div 1.536M = 0.3ms \Longrightarrow a = 60 $
综上: $ W \geq 121 \Longrightarrow n \geq 7 $, 即至少要 7 位序号

<br>

<font face = "Times New Roman" size = 4>
<b>13.</b> Consider the operation of protocol 6 over a 1-Mbps perfect (i.e., error-free) line. 
The maximum frame size is 1000 bits. New packets are generated 1 second apart. The timeout interval is 10 msec. 
If the special acknowledgement timer were eliminated, unnecessary timeouts would occur. 
How many times would the average message be transmitted?
</font>

发送一帧所需的时间是 1000/10M = 1ms，又因为每秒只有一帧要发送, 而重传间隔 10ms < 1s, 且没有ACK 定时器, 即只采用捎带确认, 所以帧重传不可避免.

假设 A 发送某一帧, B 收到后, 接收窗口滑动, 但因为没有要发送给 A 主机的帧, 则等待;
10ms 之后 A 主机重发该帧, B 收到后发现是重复帧发送 NAK;
A 收到 NAK 之后不再重发. 因此每一帧都发送两次.

<br>

<font face = "Times New Roman" size = 4>
<b>14.</b> In protocol 6, $ MAX\_SEQ = 2^n − 1 $. 
While this condition is obviously desirable to make efficient use of header bits, we have not demonstrated that it is essential. 
Does the protocol work correctly for $ MAX\_SEQ = 4 $, for example?
</font>

*本题最好结合协议代码来理解, 以下解释为我本人所写, 不是标准答案*
不能正常工作.
例如:
发送数据编号:
0 1 2 3 4 0 ......
当发送窗口滑动到 [4 0] 时, 发送方发送编号为 4 的帧, 接受方收到后会将其存放在 arrived[0] 中. 
而在接受窗口 [3 4] 时, arrived[1] 已经被标记为0, 由此 arrived数组全部为 true, 数据链路层就会上交网络层. 
而此时上交的数据的顺序是不正确的, 会出错.

<br>

<font face = "Times New Roman" size = 4>
<b>15.</b> When a file is transferred between two computers, two acknowledgement strategies are possible. 
In the first one, the file is chopped up into packets, which are individually acknowledged by the receiver, but the file transfer as a whole is not acknowledged. 
In the second one, the packets are not acknowledged individually, but the entire file is acknowledged when it arrives. 
Discuss these two approaches.
</font>

第一种机制中, 当某个分组的传输发生错误时, 可以只重发该分组, 而无需重发整个文件. 其优点是重传开销小, 但确认的开销相对第二种机制要大. 适合于网络可靠性能较差, 容易发生传输错误或丢失的情况.
第二种机制中,一旦某个分组发生错误, 则需要重传整个文件. 适合于网络传输故障率比较低的情况, 其优点是节省确认所消耗的网络资源.

<br>

<font face = "Times New Roman" size = 4>
<b>16.</b> In some networks, the data link layer handles transmission errors by requesting that damaged frames be retransmitted. 
If the probability of a frame' s being damaged is $ p $, what is the mean number of transmissions required to send a frame? 
Assume that acknowledgements are never lost.
</font>

*无穷级数的计算, 大一下 (2021) 网课阶段没怎么学好*
由题意可知, 发送一帧需要的平均传输次数为:

$$ \sum_{i = 1}^{\infty} ip^{i - 1}(1 - p) = \frac{1}{1 - p} $$


<font face = "Times New Roman" size = 4>
<b>17.</b> Frames of 1000 bits are sent over a 1-Mbps channel using a geostationary satellite whose propagation time from the earth is 270 msec.
Acknowledgements are always piggybacked onto data frames. The headers are very short. Three-bit sequence numbers are used. 
What is the maximum achievable channel utilization for <br>
(a) Stop-and-wait? <br>
(b) Protocol 5? <br>
(c) Protocol 6? <br>
</font>
$$ 发送时延 = \frac{1000}{1M} = 1 ms \quad 传播时延 = 270 ms \quad a = \frac{传播时延}{发送时延} = 270 $$

$$\begin{gather}
  \eta_{停等协议} = \frac{1}{2(1 + a)} = \frac{1}{542} = 0.18 \\% \\
  \eta_{协议5} = \frac{2^3 - 1}{2(1 + a)} = \frac{7}{542} = 1.29 \\% \\
  \eta_{协议6} = \frac{2^{3 - 1}}{2(1 + a)} = \frac{4}{542} = 0.74 \\%
\end{gather}$$


<font face = "Times New Roman" size = 4>
<b>18.</b> Consider an error-free 64-kbps satellite channel used to send 512-byte data frames in one direction, with very short acknowledgements coming back the other way. 
What is the maximum throughput for window sizes of 1, 7, 15, and 127? 
The earth-satellite propagation time is 270 msec.
</font>

$ 发送时延 = 512 \times 8 \div 64k = 64 ms, 传播时延 = 270 ms, \Longrightarrow a = 4.2 $
设发送窗户大小为 $ W, 且当 \frac{W}{1 + 2a} \geq 1 \Longrightarrow W \geq 10 $ 时, 信道利用率最高.  

$ W = 1, 吞吐量 = \frac{1}{1 + 2a} \times 64k = 6.8kbps $  

$ W = 7, 吞吐量 = \frac{7}{1 + 2a} \times 64k = 47.7kbps $  

当 $ W = 15 \\; OR \\; 127 $ 时, 信道满负荷工作, 最大吞吐量 = $ 64kbps $ 

<br>

<font face = "Times New Roman" size = 4>
<b>19.</b> A 100-km-long cable runs at the T1 data rate. The propagation speed in the cable is 2/3 the speed of light in vacuum. How many bits fit in the cable?
</font>

由题意可知, 电缆的传播速度为 $ 20 \times 10^4 km/s $, 100 公里的电缆将在 0.5 毫秒内被填满, 所以需要: $ 1.544M \times 0.5 m = 772 bits$ 即可填满电缆.
<br>

<font face = "Times New Roman" size = 4>
<b>20.</b> Give at least one reason why PPP uses byte stuffing instead of bit stuffing to prevent accidental flag bytes within the payload from causing confusion.
</font>

PPP 是由软件实现的, 而位填充几乎都是在硬件协议中实现的. 对于软件实现, 字节操作比位操作更简单.
此外, PPP是设计用于调制解调器的. 调制解调器接收和传送数据的单位是字符而不是位.

**注: 从本篇 blogs 开始, hexo markdown 渲染器更换为 'hexo-renderer-markdown-it-plus', 因为其对 LaxteX 语法有着更好的支持, 所以可能导致之前的一些 blgos 数学公式出现问题.**
**同时, 我发现, 换用此 markdown 渲染器之后, 行间公式会发生重复渲染的情况, 目前 (2023-04-19) 还无法解决这个问题.**
**还有, 目前本地渲染没有问题, 目前 (2023-04-19 14:47) 还未上传 GitHub, 不清楚 GitHub Actions 会不会有问题**

<pre class="note note-info">
<strong>2023-04-19</strong> 
<strong>IP属地: 北京</strong>
</pre>