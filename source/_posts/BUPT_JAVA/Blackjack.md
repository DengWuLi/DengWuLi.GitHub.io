---
title: "BUPT JAVA: Blackjack"
index_img: /img/BUPT.png
banner_img: /img/Java.png
date: 2023-05-23
tags:
  - Java
category:
  - BUPT_JAVA
---

# Blackjack

## 题目描述:

21 点又名黑杰克 (Blackjack), 起源于法国, 已流传到世界各地, 有着悠久的历史. 现在在世界各地的赌场中都可以看到二十一点. 随着互联网的发展, 二十一点开始走向网络时代. 该游戏由 2 到 6 个人玩, 使用除大小王之外的 52 张牌, 游戏者的目标是使手中的牌的点数之和不超过 21 点且尽量大.
大家手中扑克点数的计算规则是: 2 至 9 牌, 按其原点数计算; `K`, `Q`, `J` 和 10 牌都算作 10 点; `A` 牌 (ace) 既可算作 1 点也可算作 11 点, 由玩家自己决定 (当玩家停牌时, 点数一律视为最大而尽量不爆, 如 `A + 9` 为 20, `A + 4+ 8` 为 13, `A + 3 + A` 视为 15) .
你的任务设计基于指定策略的一个 21 点游戏的部分功能.
指定策略为: 如果手中牌的点数之和小于 17 点则继续要下一张牌, 直到大于等于 17 点为止. 如果手里的牌有 A, 且 A 的点数当成 11 点没有超过 21 点, 则此时 A 要按 11 点计算, 如果超过 21 点, 则 A 要按 1 点计算.
一个参考的设计为:

1. 设计一个 card 类, 用于保存一张牌;
2. 设计一个 hand 类, 用于保存一手牌;
3. 设计一个 player 类, 该类可以基于指定策略完成一次游戏过程.

## 输入:

若干行 (至少 2 行), 每行代表一张牌. 具体格式见样例.

## 输出:

若干行.
读入前两张牌不输出, 从第三张牌开始 (如果需要), 则每次要牌, 要先输出 `Hit`, 然后读入下一张牌, 并依次输出该牌的花色及点数 (A 输出 `1 11`, 即它有两个点数). 当不再要牌时要先输出 `Stand`, 然后在一行内输出这一手牌, 牌与牌之间用一个空格分隔. 牌输出的顺序为先看牌面, 牌面小的在前 (牌面由小到大的顺序为 A, 2, 3....J, Q, K), 当牌面相同时看花色, 输出顺序从前到后为 `Spade`, `Heart`, `Diamond`, `Club`. 最后一行输出这一手牌的结果, 如果总点数超过 21 点，则输出 `Bust`, 如果是 Blackjack (一手牌只有两张牌且点数相加和为 21 点) 则输出 `Blackjack`. 其他情况则输出一个整数, 代表这手牌的点数 (尽量大且不爆). 具体格式见样例.

## 输入样例:

```txt
Spade 4
Heart A
Heart 3
```

## 输出样例:

```txt
Hit
Heart 3
Stand
HeartA Heart3 Spade4
18
```

## Java

```java
// Blackjack
// 2023/05/22 ~ 2023/05/23

import java.util.Collections;
import java.util.Scanner;
import java.util.Vector;

public class Main {
    public static void main(String[] args) {
        var input = new Scanner(System.in);
        String color, point;
        int i = 0;
        while (input.hasNext()) {
            color = input.next();
            point = input.next();
            i++;
            if (i >= 3) {
                System.out.print(color + " ");
                switch (point) {
                    case "A" -> System.out.println("1 11");
                    case "J", "Q", "K" -> System.out.println("10");
                    default -> System.out.println(Integer.parseInt(point));
                }
            }
            Hand.add(color, point);
            var p = Hand.getPoints();
            if (i >= 2) {
                if (Hand.getPoints() < 17)
                    System.out.println("Hit");
                else {
                    System.out.println("Stand");
                    Hand.cardsPrint();
                    var points = Hand.getPoints();
                    if (points > 21)
                        System.out.println("Bust");
                    else if (points == 21 && Hand.cards.size() == 2)
                        System.out.println("Blackjack");
                    else
                        System.out.println(points);
                    break;
                }
            }
        }

    }
}

class Card implements Comparable<Card> {
    public static final String[] SUITS = {"Spade", "Heart", "Diamond", "Club"};
    int suit; // 花色
    int rank; // 点数

    Card(String suit, String rank) {
        for (int i = 0; i < SUITS.length; i++) {
            if (suit.equals(SUITS[i])) {
                this.suit = i;
                break;
            }
        }

        switch (rank) {
            case "A" -> this.rank = 1;
            case "J" -> this.rank = 11;
            case "Q" -> this.rank = 12;
            case "K" -> this.rank = 13;
            default -> this.rank = Integer.parseInt(rank);
        }
    }

    @Override
    public int compareTo(Card other) {
        if (this.rank == other.rank)
            return (this.suit < other.suit) ? -1 : 1;
        else
            return (this.rank < other.rank) ? -1 : 1;
    }
}

class Hand {
    public static final Vector<Card> cards = new Vector<>();
    private static int points = 0;
    private static int aceCount = 0;

    public static void add(String suit, String rank) {
        cards.add(new Card(suit, rank));

        switch (rank) {
            case "A" -> aceCount++;
            case "J", "Q", "K" -> points += 10;
            default -> points += Integer.parseInt(rank);
        }
    }

    public static int getPoints() {
        int res = -1;
        // 当 ACE 全部都是 1 时, 已经超过了 21 点, 就直接返回
        if (points + aceCount > 21)
            return points + aceCount;

        // 返回不超过 21 点的最大点数
        for (int i = 0; i <= aceCount; i++) {
            var tempPoint = points + i * 11 + (aceCount - i);
            if (tempPoint <= 21 && tempPoint >= res)
                res = tempPoint;
        }
        return res;
    }

    public static void cardsPrint() {
        Collections.sort(cards);
        for (Card card : cards) {
            String rank;
            switch (card.rank) {
                case 1 -> rank = "A";
                case 11 -> rank = "J";
                case 12 -> rank = "Q";
                case 13 -> rank = "K";
                default -> rank = String.valueOf(card.rank);
            }
            System.out.print(Card.SUITS[card.suit] + rank + " ");
        }
        System.out.println();
    }
}
```

<pre class="note note-info">
<strong>2023-05-23</strong> 
<strong>IP属地: 北京</strong>
</pre>
