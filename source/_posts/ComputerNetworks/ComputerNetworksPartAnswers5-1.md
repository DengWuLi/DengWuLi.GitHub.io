---
title: "Computer Networks Part Answers 5 - 1"
index_img: /img/ComputerNetworksCover.jpg
banner_img: /img/ComputerNetworksCover.jpg
date: 2023-06-18
tags:
  - ComputerNetworks
category:
  - AnswersShare
mermaid: true
---

# Computer Networks Part Answers 5 - 1

<font face = "Times New Roman" size = 4>
<b>1.</b> Are there any circumstances when connection-oriented service will (or at least should) deliver packets out of order? Explain.
</font>

可能发生错序.
在面向连接的服务中, 由于所有发往目的站的数据包都沿着相同的路径传输, 一般不会出现乱序提交的情况.
但是, 对于特殊的数据包, 如异常事件 (例如中断信号) 应该优先处理, 不排队, 不按照顺序交付.
例如在应用中, 一个用户键入退出键 (如 Ctrl-C) 时, 所产生的数据应该立即发送, 并且应当跳过当前队列中排在前面的其它数据包.

<br>

<font face = "Times New Roman" size = 4>
<b>2.</b> Consider the network of Fig. 5-12(a). Distance vector routing is used, and the following vectors have just come in to router C:
from B: (5, 0, 8, 12, 6, 2); from D: (16, 12, 6, 0, 9, 10); from E: (7, 6, 3, 9, 0, 4). <br>
The cost of the links from C to B, D, and E, are 6, 3, and 5, respectively. What is C's new routing table? Give both the outgoing line to use and the cost.
</font>

<div width="100%" style="overflow-x: auto; text-align: center;"> 
<?xml version="1.0" encoding="utf-8" standalone="no"?>
<!DOCTYPE &amp;&amp;&amp; PUBLIC "-//W3C//DTD SVG 1.1//EN"
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg xmlns:xlink="http://www.w3.org/1999/xlink" width="460.8pt" height="345.6pt" viewBox="0 0 460.8 345.6" xmlns="http://www.w3.org/2000/svg" version="1.1">
 <metadata>
  <rdf:RDF xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:cc="http://creativecommons.org/ns#" xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
   <cc:Work>
    <dc:type rdf:resource="http://purl.org/dc/dcmitype/StillImage"/>
    <dc:date>2023-06-18T20:21:49.933794</dc:date>
    <dc:format>image/svg+xml</dc:format>
    <dc:creator>
     <cc:Agent>
      <dc:title>Matplotlib v3.6.2, https://matplotlib.org/</dc:title>
     </cc:Agent>
    </dc:creator>
   </cc:Work>
  </rdf:RDF>
 </metadata>
 <defs>
  <style type="text/css">*{stroke-linejoin: round; stroke-linecap: butt}</style>
 </defs>
 <g id="figure_1">
  <g id="patch_1">
   <path d="M 0 345.6 
L 460.8 345.6 
L 460.8 0 
L 0 0 
z
" style="fill: #ffffff"/>
  </g>
  <g id="axes_1">
   <g id="patch_2">
    <path d="M 57.6 307.584 
L 414.72 307.584 
L 414.72 41.472 
L 57.6 41.472 
z
" style="fill: #ffffff"/>
   </g>
   <g id="matplotlib.axis_1"/>
   <g id="matplotlib.axis_2"/>
   <g id="line2d_1">
    <path d="M 164.736 263.232 
L 307.584 263.232 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_2">
    <path d="M 307.584 263.232 
L 379.008 174.528 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_3">
    <path d="M 379.008 174.528 
L 307.584 85.824 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_4">
    <path d="M 307.584 85.824 
L 164.736 85.824 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_5">
    <path d="M 164.736 85.824 
L 93.312 174.528 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_6">
    <path d="M 93.312 174.528 
L 164.736 263.232 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_7">
    <path d="M 164.736 85.824 
L 307.584 263.232 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="line2d_8">
    <path d="M 307.584 85.824 
L 164.736 263.232 
" clip-path="url(#p14159a570c)" style="fill: none; stroke: #ff0000; stroke-width: 1.5; stroke-linecap: square"/>
   </g>
   <g id="patch_3">
    <path d="M 57.6 307.584 
L 57.6 41.472 
" style="fill: none; stroke: #000000; stroke-width: 0.8; stroke-linejoin: miter; stroke-linecap: square"/>
   </g>
   <g id="patch_4">
    <path d="M 414.72 307.584 
L 414.72 41.472 
" style="fill: none; stroke: #000000; stroke-width: 0.8; stroke-linejoin: miter; stroke-linecap: square"/>
   </g>
   <g id="patch_5">
    <path d="M 57.6 307.584 
L 414.72 307.584 
" style="fill: none; stroke: #000000; stroke-width: 0.8; stroke-linejoin: miter; stroke-linecap: square"/>
   </g>
   <g id="patch_6">
    <path d="M 57.6 41.472 
L 414.72 41.472 
" style="fill: none; stroke: #000000; stroke-width: 0.8; stroke-linejoin: miter; stroke-linecap: square"/>
   </g>
   <g id="text_1">
    <!-- E -->
    <g transform="translate(160.94475 266.54325) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-45" d="M 628 4666 
L 3578 4666 
L 3578 4134 
L 1259 4134 
L 1259 2753 
L 3481 2753 
L 3481 2222 
L 1259 2222 
L 1259 531 
L 3634 531 
L 3634 0 
L 628 0 
L 628 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-45"/>
    </g>
   </g>
   <g id="text_2">
    <!-- F -->
    <g transform="translate(304.133062 266.54325) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-46" d="M 628 4666 
L 3309 4666 
L 3309 4134 
L 1259 4134 
L 1259 2759 
L 3109 2759 
L 3109 2228 
L 1259 2228 
L 1259 0 
L 628 0 
L 628 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-46"/>
    </g>
   </g>
   <g id="text_3">
    <!-- D -->
    <g transform="translate(374.388 177.83925) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-44" d="M 1259 4147 
L 1259 519 
L 2022 519 
Q 2988 519 3436 956 
Q 3884 1394 3884 2338 
Q 3884 3275 3436 3711 
Q 2988 4147 2022 4147 
L 1259 4147 
z
M 628 4666 
L 1925 4666 
Q 3281 4666 3915 4102 
Q 4550 3538 4550 2338 
Q 4550 1131 3912 565 
Q 3275 0 1925 0 
L 628 0 
L 628 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-44"/>
    </g>
   </g>
   <g id="text_4">
    <!-- C -->
    <g transform="translate(303.394313 89.13525) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-43" d="M 4122 4306 
L 4122 3641 
Q 3803 3938 3442 4084 
Q 3081 4231 2675 4231 
Q 1875 4231 1450 3742 
Q 1025 3253 1025 2328 
Q 1025 1406 1450 917 
Q 1875 428 2675 428 
Q 3081 428 3442 575 
Q 3803 722 4122 1019 
L 4122 359 
Q 3791 134 3420 21 
Q 3050 -91 2638 -91 
Q 1578 -91 968 557 
Q 359 1206 359 2328 
Q 359 3453 968 4101 
Q 1578 4750 2638 4750 
Q 3056 4750 3426 4639 
Q 3797 4528 4122 4306 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-43"/>
    </g>
   </g>
   <g id="text_5">
    <!-- B -->
    <g transform="translate(160.619438 89.13525) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-42" d="M 1259 2228 
L 1259 519 
L 2272 519 
Q 2781 519 3026 730 
Q 3272 941 3272 1375 
Q 3272 1813 3026 2020 
Q 2781 2228 2272 2228 
L 1259 2228 
z
M 1259 4147 
L 1259 2741 
L 2194 2741 
Q 2656 2741 2882 2914 
Q 3109 3088 3109 3444 
Q 3109 3797 2882 3972 
Q 2656 4147 2194 4147 
L 1259 4147 
z
M 628 4666 
L 2241 4666 
Q 2963 4666 3353 4366 
Q 3744 4066 3744 3513 
Q 3744 3084 3544 2831 
Q 3344 2578 2956 2516 
Q 3422 2416 3680 2098 
Q 3938 1781 3938 1306 
Q 3938 681 3513 340 
Q 3088 0 2303 0 
L 628 0 
L 628 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-42"/>
    </g>
   </g>
   <g id="text_6">
    <!-- A -->
    <g transform="translate(89.207625 177.83925) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-41" d="M 2188 4044 
L 1331 1722 
L 3047 1722 
L 2188 4044 
z
M 1831 4666 
L 2547 4666 
L 4325 0 
L 3669 0 
L 3244 1197 
L 1141 1197 
L 716 0 
L 50 0 
L 1831 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-41"/>
    </g>
   </g>
   <g id="text_7">
    <!-- 8 -->
    <g transform="translate(232.3425 266.54325) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-38" d="M 2034 2216 
Q 1584 2216 1326 1975 
Q 1069 1734 1069 1313 
Q 1069 891 1326 650 
Q 1584 409 2034 409 
Q 2484 409 2743 651 
Q 3003 894 3003 1313 
Q 3003 1734 2745 1975 
Q 2488 2216 2034 2216 
z
M 1403 2484 
Q 997 2584 770 2862 
Q 544 3141 544 3541 
Q 544 4100 942 4425 
Q 1341 4750 2034 4750 
Q 2731 4750 3128 4425 
Q 3525 4100 3525 3541 
Q 3525 3141 3298 2862 
Q 3072 2584 2669 2484 
Q 3125 2378 3379 2068 
Q 3634 1759 3634 1313 
Q 3634 634 3220 271 
Q 2806 -91 2034 -91 
Q 1263 -91 848 271 
Q 434 634 434 1313 
Q 434 1759 690 2068 
Q 947 2378 1403 2484 
z
M 1172 3481 
Q 1172 3119 1398 2916 
Q 1625 2713 2034 2713 
Q 2441 2713 2670 2916 
Q 2900 3119 2900 3481 
Q 2900 3844 2670 4047 
Q 2441 4250 2034 4250 
Q 1625 4250 1398 4047 
Q 1172 3844 1172 3481 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-38"/>
    </g>
   </g>
   <g id="text_8">
    <!-- 7 -->
    <g transform="translate(339.4785 222.19125) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-37" d="M 525 4666 
L 3525 4666 
L 3525 4397 
L 1831 0 
L 1172 0 
L 2766 4134 
L 525 4134 
L 525 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-37"/>
    </g>
   </g>
   <g id="text_9">
    <!-- 3 -->
    <g transform="translate(339.4785 133.48725) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-33" d="M 2597 2516 
Q 3050 2419 3304 2112 
Q 3559 1806 3559 1356 
Q 3559 666 3084 287 
Q 2609 -91 1734 -91 
Q 1441 -91 1130 -33 
Q 819 25 488 141 
L 488 750 
Q 750 597 1062 519 
Q 1375 441 1716 441 
Q 2309 441 2620 675 
Q 2931 909 2931 1356 
Q 2931 1769 2642 2001 
Q 2353 2234 1838 2234 
L 1294 2234 
L 1294 2753 
L 1863 2753 
Q 2328 2753 2575 2939 
Q 2822 3125 2822 3475 
Q 2822 3834 2567 4026 
Q 2313 4219 1838 4219 
Q 1578 4219 1281 4162 
Q 984 4106 628 3988 
L 628 4550 
Q 988 4650 1302 4700 
Q 1616 4750 1894 4750 
Q 2613 4750 3031 4423 
Q 3450 4097 3450 3541 
Q 3450 3153 3228 2886 
Q 3006 2619 2597 2516 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-33"/>
    </g>
   </g>
   <g id="text_10">
    <!-- 2 -->
    <g transform="translate(232.3425 89.13525) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-32" d="M 1228 531 
L 3431 531 
L 3431 0 
L 469 0 
L 469 531 
Q 828 903 1448 1529 
Q 2069 2156 2228 2338 
Q 2531 2678 2651 2914 
Q 2772 3150 2772 3378 
Q 2772 3750 2511 3984 
Q 2250 4219 1831 4219 
Q 1534 4219 1204 4116 
Q 875 4013 500 3803 
L 500 4441 
Q 881 4594 1212 4672 
Q 1544 4750 1819 4750 
Q 2544 4750 2975 4387 
Q 3406 4025 3406 3419 
Q 3406 3131 3298 2873 
Q 3191 2616 2906 2266 
Q 2828 2175 2409 1742 
Q 1991 1309 1228 531 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-32"/>
    </g>
   </g>
   <g id="text_11">
    <!-- 4 -->
    <g transform="translate(125.2065 133.48725) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-34" d="M 2419 4116 
L 825 1625 
L 2419 1625 
L 2419 4116 
z
M 2253 4666 
L 3047 4666 
L 3047 1625 
L 3713 1625 
L 3713 1100 
L 3047 1100 
L 3047 0 
L 2419 0 
L 2419 1100 
L 313 1100 
L 313 1709 
L 2253 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-34"/>
    </g>
   </g>
   <g id="text_12">
    <!-- 5 -->
    <g transform="translate(125.2065 222.19125) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-35" d="M 691 4666 
L 3169 4666 
L 3169 4134 
L 1269 4134 
L 1269 2991 
Q 1406 3038 1543 3061 
Q 1681 3084 1819 3084 
Q 2600 3084 3056 2656 
Q 3513 2228 3513 1497 
Q 3513 744 3044 326 
Q 2575 -91 1722 -91 
Q 1428 -91 1123 -41 
Q 819 9 494 109 
L 494 744 
Q 775 591 1075 516 
Q 1375 441 1709 441 
Q 2250 441 2565 725 
Q 2881 1009 2881 1497 
Q 2881 1984 2565 2268 
Q 2250 2553 1709 2553 
Q 1456 2553 1204 2497 
Q 953 2441 691 2322 
L 691 4666 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-35"/>
    </g>
   </g>
   <g id="text_13">
    <!-- 6 -->
    <g transform="translate(271.872 227.998125) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-36" d="M 2113 2584 
Q 1688 2584 1439 2293 
Q 1191 2003 1191 1497 
Q 1191 994 1439 701 
Q 1688 409 2113 409 
Q 2538 409 2786 701 
Q 3034 994 3034 1497 
Q 3034 2003 2786 2293 
Q 2538 2584 2113 2584 
z
M 3366 4563 
L 3366 3988 
Q 3128 4100 2886 4159 
Q 2644 4219 2406 4219 
Q 1781 4219 1451 3797 
Q 1122 3375 1075 2522 
Q 1259 2794 1537 2939 
Q 1816 3084 2150 3084 
Q 2853 3084 3261 2657 
Q 3669 2231 3669 1497 
Q 3669 778 3244 343 
Q 2819 -91 2113 -91 
Q 1303 -91 875 529 
Q 447 1150 447 2328 
Q 447 3434 972 4092 
Q 1497 4750 2381 4750 
Q 2619 4750 2861 4703 
Q 3103 4656 3366 4563 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-36"/>
    </g>
   </g>
   <g id="text_14">
    <!-- 1 -->
    <g transform="translate(200.448 227.998125) scale(0.12 -0.12)">
     <defs>
      <path id="DejaVuSans-31" d="M 794 531 
L 1825 531 
L 1825 4091 
L 703 3866 
L 703 4441 
L 1819 4666 
L 2450 4666 
L 2450 531 
L 3481 531 
L 3481 0 
L 794 0 
L 794 531 
z
" transform="scale(0.015625)"/>
     </defs>
     <use xlink:href="#DejaVuSans-31"/>
    </g>
   </g>
  </g>
 </g>
 <defs>
  <clipPath id="p14159a570c">
   <rect x="57.6" y="41.472" width="357.12" height="266.112"/>
  </clipPath>
 </defs>
</svg>
</div>

由题意, 我们可以列出下面这个表格:

<table>
<thead>
  <tr>
    <th rowspan="3">目的地</th>
    <th colspan="3">延迟</th>
    <th rowspan="3">最终选择</th>
    <th rowspan="3">时延</th>
  </tr>
  <tr>
    <th colspan="3">数据来源(括号内为传输延迟)</th>
  </tr>
  <tr>
    <th>B(6)</th>
    <th>D(3)</th>
    <th>E(5)</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>A</td>
    <td>5</td>
    <td>16</td>
    <td>7</td>
    <td>B</td>
    <td>11</td>
  </tr>
  <tr>
    <td>B</td>
    <td>0</td>
    <td>12</td>
    <td>6</td>
    <td>B</td>
    <td>6</td>
  </tr>
  <tr>
    <td>C</td>
    <td>8</td>
    <td>6</td>
    <td>3</td>
    <td>C</td>
    <td>--</td>
  </tr>
  <tr>
    <td>D</td>
    <td>12</td>
    <td>0</td>
    <td>9</td>
    <td>D</td>
    <td>3</td>
  </tr>
  <tr>
    <td>E</td>
    <td>6</td>
    <td>9</td>
    <td>0</td>
    <td>E</td>
    <td>5</td>
  </tr>
  <tr>
    <td>F</td>
    <td>2</td>
    <td>10</td>
    <td>4</td>
    <td>B</td>
    <td>8</td>
  </tr>
</tbody>
</table>

C 的路由表为:

| 目的地 | 延迟 | 下一跳 |
|:---:|:--:|:---:|
|  A  | 11 |  B  |
|  B  | 6  |  B  |
|  C  | 0  | --  |
|  D  | 3  |  D  |
|  E  | 5  |  E  |
|  F  | 8  |  B  |

附, 一个用于画出上图的 Python 代码:

```python
import matplotlib.pyplot as plt


def draw_hexagon():
    # 定义六边形的顶点坐标
    x = [-1, 1, 2, 1, -1, -2]
    y = [0, 0, 1, 2, 2, 1]

    # 创建一个图形对象
    fig, ax = plt.subplots()

    # 绘制六边形
    # ax.fill(x, y, 'b', alpha=0.5)  # 使用蓝色填充，透明度为0.5

    # 在每个顶点上标注字母标记
    labels = ['E', 'F', 'D', 'C', 'B', 'A']
    for i in range(len(x)):
        ax.text(x[i], y[i], labels[i], ha='center', va='center', fontsize=12)

    # 连接六边形的边
    ax.plot([x[0], x[1]], [y[0], y[1]], 'r-')  # 连接 A-B
    ax.plot([x[1], x[2]], [y[1], y[2]], 'r-')  # 连接 B-C
    ax.plot([x[2], x[3]], [y[2], y[3]], 'r-')  # 连接 C-D
    ax.plot([x[3], x[4]], [y[3], y[4]], 'r-')  # 连接 D-E
    ax.plot([x[4], x[5]], [y[4], y[5]], 'r-')  # 连接 E-F
    ax.plot([x[5], x[0]], [y[5], y[0]], 'r-')  # 连接 F-A
    ax.plot([x[4], x[1]], [y[4], y[1]], 'r-')  # 连接 B-F
    ax.plot([x[3], x[0]], [y[3], y[0]], 'r-')  # 连接 C-E
    # 在边和对角线上标记数字
    ax.text((x[0] + x[1]) / 2, (y[0] + y[1]) / 2, '8', ha='center', va='center', fontsize=12, color='black')
    ax.text((x[1] + x[2]) / 2, (y[1] + y[2]) / 2, '7', ha='center', va='center', fontsize=12, color='black')
    ax.text((x[2] + x[3]) / 2, (y[2] + y[3]) / 2, '3', ha='center', va='center', fontsize=12, color='black')
    ax.text((x[3] + x[4]) / 2, (y[3] + y[4]) / 2, '2', ha='center', va='center', fontsize=12, color='black')
    ax.text((x[4] + x[5]) / 2, (y[4] + y[5]) / 2, '4', ha='center', va='center', fontsize=12, color='black')
    ax.text((x[5] + x[0]) / 2, (y[5] + y[0]) / 2, '5', ha='center', va='center', fontsize=12, color='black')

    ax.text((x[4] + 3 * x[1]) / 4, (y[4] + 3 * y[1]) / 4, '6', ha='left', va='top', fontsize=12, color='black')
    ax.text((x[3] + 3 * x[0]) / 4, (y[3] + 3 * y[0]) / 4, '1', ha='left', va='top', fontsize=12, color='black')

    # 设置坐标轴范围
    ax.set_xlim(-2.5, 2.5)
    ax.set_ylim(-0.5, 2.5)

    # 设置坐标轴刻度标签为空
    ax.set_xticks([])
    ax.set_yticks([])

    plt.savefig('题2.svg', format='svg')

    # 显示图形
    plt.show()


# 调用函数绘制六边形
draw_hexagon()
```

<br>

<font face = "Times New Roman" size = 4>
<b>3.</b> For hierarchical routing with 4800 routers, what region and cluster sizes should be chosen to minimize the size of the routing table for a three-layer hierarchy?
A good starting place is the hypothesis that a solution with k clusters of k regions of k routers is close to optimal, which means that k is about the cube root of 4800 (around 16). 
Use trial and error to check out combinations where all three parameters are in the general vicinity of 16.
</font>

经过试验, 最佳方案是 $ 4800 = 15 \times 16 \times 20 $, 即, 当选择 15 个簇, 16 个区域, 每个区域 20 个路由器时, 路由表尺寸最小.
路由表表项为也可选择 20 个簇, 16 个区, 每区 15 个路由器, 总表项长度一样, 为 49 (15 + 16 + 20 - 2), 以此类推, 一共 6 种组合.
这里为什么还有个 `-2` 而不是 `-3` 呢, 因为每一层的路由器都不需要在路由表里构建自己的信息啊. 可以这样想, 在 "簇" 这一层,
每个路由器只需要保存除自己外其他同层路由器的信息, "区" 这一层也是如此, 但是情况到了 "区" 这一层则有所变化了. "区"
这一层的路由器除了需要保存 19 个本层的路由器. 还需要保存一个与其所在区相连的区一级别的路由器的路由信息.
所以最后计算结果需要 `-2` 而不是 `-3`.

<br>

<font face = "Times New Roman" size = 4>
<b>4.</b> A datagram network allows routers to drop packets whenever they need to. The probability of a router discarding a packet is $ p $. 
Consider the case of a source host connected to the source router, which is connected to the destination router, and then to the destination host. 
If either of the routers discards a packet, the source host eventually times out and tries again. 
If both host-router and router-router lines are counted as hops, what is the mean number of <br>
(a) hops a packet makes per transmission? <br>
(b) transmissions a packet makes? <br>
(c) hops required per received packet?
</font>

(a): 一帧经过的跳数可能是: 1, 2, 3. 概率分别为:
$$ P_1 = p \quad P_2 = (1 - p)p \quad P_3 = (1 - p)p^2 $$
则传输过程中, 每个包的平均跳数为:
$$ averageHops = \frac{P_1 + 2P_2 + 3P_3}{3} = p^2 - 3p + 3 $$

(b): 一个包要想正确传达, 需要经历三跳, 每个包正确到达的概率为 $ P_3 $, 则, 每个包产生的传输次数:
$$ \sum^{\infty}_{i = 1} i \times ((1 - p)^2)^i = \frac{1}{(1 - p)^2} $$
如下图所示:

\(c\): 由 a, b 两小问可知, 每个包送达的总跳数为:
$$ \frac{p^2 - 3p + 3}{(1 - p)^2} $$

<br>

<font face = "Times New Roman" size = 4>
<b>5.</b> Describe the two main differences between the Explicit Congestion Notification (ECN) and Random Early Detection (RED).
</font>

1. ECN 通过在 IP 包中设定通知位, 明确地 (显式) 发送拥塞通知给源主机. 而 RED 通过丢弃数据包来隐式地通知源主机发生拥塞.
2. ECN 只在路由器的缓冲空间耗尽 (队列满) 时丢弃数据包; RED 则是在剩余缓存达到临界值, 而不是耗尽时丢弃数据包.

<br>

<font face = "Times New Roman" size = 4>
<b>6.</b> Imagine a flow specification that has a maximum packet size of 1000 bytes, a token bucket rate of 10 million bytes/sec, a token bucket size of 1 million bytes, and a maximum transmission rate of 50 million bytes/sec. 
How long can a burst at maximum speed last?
</font>

设能持续 t 秒. 由题可知: $ 50M \times t = 1M + 10M \times t $, 解得 $ t = 0.025 $, 最长能持续 25 ms.

<br>

<font face = "Times New Roman" size = 4>
<b>7.</b> Suppose that host A is connected to a router R1, R1 is connected to another router, R2, and R2 is connected to host B. 
Suppose that a TCP message that contains 900 bytes of data and 20 bytes of TCP header is passed to the IP code at host A for delivery to B. 
Show the Total length, Identification, DF, MF, and Fragment offset fields of the IP header in each packet transmitted over the three links.
Assume that link A-R1 can support a maximum frame size of 1024 bytes including a 14-byte frame header, 
link R1-R2 can support a maximum frame size of 512 bytes, including an 8-byte frame header, 
and link R2-B can support a maximum frame size of 512 bytes including a 12-byte frame header.
</font>

1. A -> R1: MTU = 1010 Bytes (1024 - 14), 一个 IP 报文能承载的最大数据为: 980 Bytes (1010 - 20), 从传输层获得的数据最长为
   920 Bytes (20 + 900). 所以只需发送一个包即可.
   总长度: 940 Bytes (20 + 920), ID = 任意值; DF, MF, Offset = (0, 0, 0).
2. R1 -> R2: MTU = 504 Bytes (512 - 8), 一个 IP 报文能承载的最大数据为: 484 Bytes (504 - 20), 所以需要发送多个数据包.
    1. 总长度: 500 Bytes (20 + 480), **这里解释一下为什么要数据部分长度为 400.** 因为所能承载最大数据的 484, 不能被 8
       整除, 所以选择距离 484 最近, 小于 484, 且可以被 8 整除的最大整数.
       ID = X; DF, MD, Offset = (0, 1, 0)
    2. 总长度: 460 Bytes (20 + 440), ID = X; DF, MD, Offset = (0, 0, 60). **这个 Offset 的计算方式就是 480/8**
3. R2 -> B: MTU = 500 Bytes (512 - 8 ), 一个 IP 报文能承载的最大数据为: 480 Bytes (500 - 20), 所以需要发送多个数据包.
    1. 总长度: 500 Bytes (20 + 480), ID = X; DF, MD, Offset = (0, 0, 0).
    2. 总长度: 460 Bytes (20 + 440), ID = X; DF, MD, Offset = (0, 0, 60).

<br>

<font face = "Times New Roman" size = 4>
<b>8.</b> A router is blasting out IP packets whose total length (data plus header) is 1024 bytes. 
Assuming that packets live for 10 sec, what is the maximum line speed the router can operate at without danger of cycling through the IP datagram ID number space?
</font>

IP 字段中 ID 占 16 bits, 所以共有 65536 个 ID, 最多能产生 65536 个不同 ID 的包, 所以最大传输速度为: $ (65536 \times 1024
\times 8) \div 10 = 54 Gbps $.

<br>

<font face = "Times New Roman" size = 4>
<b>9.</b> Suppose that instead of using 16 bits for the network part of a class B address originally, 20 bits had been used. 
How many class B networks would there have been?
</font>

如果使用 20 位网络号, 除去2位的B类地址标识, 有 18 位留给网络. 因此, 网络数量将是 $ 2^18 $ 或 262144 个.

<br>

<font face = "Times New Roman" size = 4>
<b>10.</b> Convert the IP address whose hexadecimal representation is C22F1582 to dotted decimal notation.
</font>

194.47.21.130
<pre class="note note-info">
<strong>2023-06-18</strong> 
<strong>IP属地: 北京</strong>
</pre>
