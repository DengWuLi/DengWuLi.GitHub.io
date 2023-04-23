---
title: 'Computer Networks Part Answers 3 - 3'
index_img: /img/ComputerNetworksCover.jpg
banner_img: /img/ComputerNetworksCover.jpg
date: 2023-04-19
tags:
  - ComputerNetworks
category:
  - AnswersShare
---
# Computer Networks Part Answers 3 - 3

<font face = "Times New Roman" size = 4>
<b>21.</b> What is the minimum overhead to send an IP packet using PPP? Count only the overhead introduced by PPP itself, not the IP header overhead.
What is the maximum overhead?
</font>

最小开销: 每一帧有 2 个标志字节, 1 个协议字节和 2 个校验字节, 每帧总共 5 字节开销.
最大开销: 2 个标志字节, 1 个地址字节, 1 个控制字节, 2 个协议字节和 4 个校验字节, 一共 10 字节开销.
附 PPP 协议帧约定:
| Flag (01111110) | Address (11111111) | Control (00000011) |     Protocol      |  Payload   |      Checksun      | Flag (01111110) |
| :-------------: | :----------------: | :----------------: | :---------------: | :--------: | :----------------: | :-------------: |
|     1 Byte      |       1 Byte       |       1 Byts       | 1 Byte OR 2 Bytes | Changeable | 2 Bytes OR 4 Bytes |     1 Byte      |

**因为 `Address` 和 `Control` 字段总是取默认配置的常数, 因此 LCP 提供了某种必要的机制, 允许通信双方就是否省略这两个字段进行协商, 去掉的话可以为每帧节省 2 个字节的空间.**

<br>

<font face = "Times New Roman" size = 4>
<b>22.</b> 已知数据位流为 $ 1101 0110 $, 采用 CRC 校验, $ G(x) = x^3 + 1 $, 计算出校验位.
</font>

非常简单, 答案: $ 111 $.

<br>

<font face = "Times New Roman" size = 4>
<b>23.</b> 采用 3 比特序号的 SR 协议, 若接收窗口为 5, 则发送窗口的最大值是多少?
</font>

使用 n 位序号的选择传协议的滑动窗口个数应满足:
$ W_T + W_R \leq 2^n $, 对于 3 位序号, $ W_T + W_R \leq 8 $, $ W_R = 5, W_T \leq 3 $

<br>

<font face = "Times New Roman" size = 4>
<b>24.</b> $ 50kbps $ 的卫星信道, 往返时延为 $ 500 ms $, 帧长为 $ 1000 $ 位, 使用 SR 协议, 若使效率达到 $ 50 \% $, 序号的比特数至少是多少?
</font>

因题目中没有强调使用忽略发送时间的 ACK 帧来确认, 假定为捎带确认.
$ a = \frac{传播时延}{发送时延} = \frac{250}{1000 \div 50} = 12.5 $
设发送窗口为 $ W $, 选择重传协议的信道利用率为 $ \frac{W}{2 + 2a} = 50 \% $, 可求出 $ W = 14 $  
$ W \leq 2^n - 1 \therefore n = 5 $

<br>

<font face = "Times New Roman" size = 4>
<b>25.</b> 数据链路层采用 GBN 协议, 发送方已经发送了编号为 0-7 的帧, 当计时器超时时, 若发送方只收到 0, 4, 5 号帧的确认, 则发送方需要重发的帧数是多少?
</font>

对 5 号帧的确认说明, 5 号帧及以前的帧全部正确接收, 因此发送方需要重发未确认的 6 号和 7 号帧, 即需要重发的帧数是 2.

<br>

<font face = "Times New Roman" size = 4>
<b>26.</b> 两台计算机的数据链路层协议实体采取滑动窗口机制. 利用 16kbps 的卫星信道传输长度为 128 字节的数据帧, 信道传播时延为270ms. <br>
(1) 计算使用停等协议的信道利用率; <br>
(2) 计算使用发送窗口为 7 的 GBN 协议的信道利用率; <br>
(3) 计算使用发送窗口为 15 的 GBN 协议的信道利用率; <br>
(4) 为使信道利用率达到最高,使 用 GBN 协议时序号的比特数最 少为多少位?
</font>

$$ 发送时延 = \frac{128 \times 8}{16k} = 64 ms \quad 传播时延 = 270 ms \quad a = \frac{传播时延}{发送时延} = 4.2 \quad 2 + 2a = 10.4 $$

$$\begin{gather}
  \eta_{停等协议} = \frac{1}{2(1 + a)} = \frac{1}{10.4} \approx 9.6 \\% \\
  \eta_{GBN7} = \frac{7}{2(1 + a)} = \frac{7}{10.4} \approx 67.3 \\% \\
\end{gather}$$

(3) 因为 15 > 10.4, 因此信道利用率为 1
(4) $ W = 2^n - 1 \geq 10.4, \therefore n \geq 4 $

<font face = "Times New Roman" size = 4>
<b>27.</b> 某数据链路层协议要传输下列 4 个字符数据: $ A: 01000111; B: 11100011; ESC: 11100000; FLAG: 01111110 $,
写出下列成帧方法中实际传输的二进制序列: <br>
(1) 字符计数法 <br>
(2) 带首尾标志的字节填充法 <br>
(3) 带首尾标志的比特填充法 <br>
(4) RS-232 协议,每次发送一个 8 位字符, 以位 `0` 为起始位位 `1` 为终止位并计算上述每种方法的效率.
</font>
以下答案中, 红色字符为填充字符

(1)  $ \textcolor{red}{00000101} \quad 01000111 \quad 11100011 \quad 11100000 \quad 01111110 $
填充字符解释: 连同字符统计字符在内共 5 个字符, 所以填二进制的5
增加了一个长度字节, 效率为 4/5 = 80%

(2) $ \textcolor{red}{01111110} \quad 01000111 \quad 11100011 \quad \textcolor{red}{11100000} \quad 11100000 \quad  \textcolor{red}{11100000}  \quad 01111110 \quad \textcolor{red}{01111110} $
增加了首尾标志和2个转义字符, 效率为 4/8 = 50%

01111110 01000111 110100011 111000000 011111010 01111110
(3) $ \textcolor{red}{01111110} \quad 01000111 \quad 11\textcolor{blue}{0}10001 \quad 1111\textcolor{blue}{0}000 \quad 0011111\textcolor{blue}{0}1 \quad 0 \quad \textcolor{red}{01111110} $
增加了首尾标志和 3 位填充, 效率为 32/51 = 62.75%

(4) RS232: 每个字符前面加 1 位起始位, 后面加 1 位停止位 
$ \textcolor{red}{0}01000111\textcolor{red}{1} \quad \textcolor{red}{0}11100011\textcolor{red}{1} \quad \textcolor{red}{0}11100000\textcolor{red}{1} \quad \textcolor{red}{0}01111110\textcolor{red}{1} $
效率为 32/40 = 80%

<pre class="note note-info">
<strong>2023-04-19</strong> 
<strong>IP属地: 北京</strong>
</pre>